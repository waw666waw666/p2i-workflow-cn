# Contributing

Thanks for contributing to `p2i-workflow`.

## What to contribute

Good contributions include:

- New prompt workflow examples
- Better wording for Prompt 1 or workflow docs
- More stable output rules for common image categories
- Compatibility notes for image tools
- Documentation fixes and translation improvements

## What not to contribute

Please avoid:

- Turning this repository into a web app or backend project
- Adding unrelated tooling or speculative features
- Copying raw prompts from third-party prompt gallery websites
- Reintroducing old three-window naming
- Breaking the one-code-block output rule

## Rules for changes

- Keep the two-window workflow: `A窗口` and `B窗口`
- Preserve the core role of Prompt 1 as a prompt-generation template
- Keep the repository documentation-first
- Match the existing concise style
- Prefer surgical edits over broad rewrites

## Adding examples

When adding a new example:

1. Start from a rough idea
2. Include the full Prompt 2 output structure
3. Keep exactly one code block in the example output
4. Include a category-appropriate `Negative Prompt`
5. Add a short quality check section

## Pull request checklist

- The workflow still uses only `A窗口` and `B窗口`
- The output contract is unchanged unless intentionally documented
- No raw third-party prompt dumping
- README links still work
- New examples are readable and copy-ready
