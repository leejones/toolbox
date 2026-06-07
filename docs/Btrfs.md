# Btrfs

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
