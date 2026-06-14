# Btrfs

## Terminology

- **subvolume** - Independent mountable partition-like dataset within a btrfs volume.
- **referenced** - All data a subvolume contains.  May be shared by other subvolumes.
- **exclusive** - Data that's unique to a subvolume, i.e. not shared by any other subvolumes.
- **snapshot** - A subvolume that's a read-only copy of another subvolume.
  - If the original subvolume changes, the snapshot remains unchanged.
  - They diverge through copy-on-write (CoW) behavior.
  - For example, if you have subvolume `@home` and create a snapshot `@home-snap`, now you have 2 subvolumes:
    - `@home` - referenced: 50G, exclusive: 0G
    - `@home-snap` - referenced: 50G, exclusive: 0G
  - Then if you add a 1G file named `file1.txt` to `@home`:
    - `@home` - referenced: 51G, exclusive: 1G (50G shared by both + 1G only on @home)
    - `@home-snap` - referenced: 50G, exclusive: 0G (50G shared by both)
    - Both point to the same underlying 50G, but `@home` also points to an additional 1G.
  - Then if you delete a 3G file named `file2.txt`:
    - `@home` - referenced: 48G, exclusive: 1G (47G shared by both + 1G only on @home)
    - `@home-snap` - referenced: 50G, exclusive: 3G (47G shared by both + 3G only on @home-snap)

## Adding a New Subvolume

Create the subvolume:

```sh
sudo btrfs subvolume create /data/@docker
```
The `@<name>` format is conventional to indicate this is a subvolume.

Create a mount point:

```sh
mkdir -p /data/docker
```

Add to `/etc/fstab`:

```
# Ensure that /data is mounted first since that's the volume where the subvolumes are located.
UUID=92e54c04-4ecc-477a-b1b3-39196add2e69 /data           btrfs   defaults		   0       2

# Mount the subvolume.
UUID=92e54c04-4ecc-477a-b1b3-39196add2e69 /data/docker    btrfs   defaults,subvol=@docker  0       2
```

Mount it:

```sh
sudo mount -a
```

Verify it:

```sh
lsblk
```

## Adding Quotas for Subvolumes

```sh
# 1. Enable quotas (once, on first setup)
sudo btrfs quota enable /data

# 2. Set limits
sudo btrfs qgroup limit 100G /data/docker
sudo btrfs qgroup limit 500G /data/nas

# 3. Verify limits
sudo btrfs qgroup show -reF /data/docker
sudo btrfs qgroup show -reF /data/nas
```
