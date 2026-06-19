# AI-Assisted Software Engineering

## Skills

- `disable-model-invocation: true` in the front matter (i.e. header)
  - Indicates this should only be invoked by the user.
  - Prevents the model from loading and invoking the skill on it's own.
  - Reduces unnecessary context usage.
  - Example:

  ```markdown
  ---
  name: my-awesome-skill
  description: A description of the skill.
  disable-model-invocation: true
  ---

  Deatils about the skill...
  ```

## References

- Matt Pocock's [skills repo](https://github.com/mattpocock/skills).
- Matt Pocock's [AI Hero website](https://www.aihero.dev/).
