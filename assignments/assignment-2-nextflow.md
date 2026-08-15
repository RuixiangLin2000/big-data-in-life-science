# Assignment 2: Scientific Workflows with Nextflow

## Goal

Practice parameterized, reproducible mass-spectrometry preprocessing in two parts:

1. Refactor an existing XCMS workflow so selected values come from configuration or command-line parameters.
2. Build an equivalent four-stage OpenMS workflow from scratch.

## Part 1: Parameterization

The original workflow contains values for peak-width limits, noise threshold, and ionization polarity. Move these values into the configuration layer and expose them as workflow parameters.

Key idea:

```text
defaults in configuration
        +
optional command-line overrides
        |
        v
process script reads params
```

The submission requirements represented in the supplied material include the modified workflow, configuration, and a record of the invocation. This repository does not publish the completed student implementation.

## Part 2: OpenMS dataflow

### Required logical stages

1. **Feature detection**
   - one mass-spectrometry input file per task
   - one reusable feature-finder parameter file
   - one feature file per input

2. **Alignment**
   - collect all feature files
   - run one alignment task across the collection
   - emit one aligned feature file per input
   - request sufficient memory

3. **Linking**
   - collect aligned feature files
   - merge them into one consensus file
   - request sufficient memory

4. **Export**
   - convert the consensus file to a table
   - clean the exported table
   - publish only the final cleaned result

## Nextflow concepts assessed

- File and value/queue channels
- Reusing a parameter input with multiple data items
- `collect` for all-at-once stages
- Constructing input and output argument lists
- Process inputs and outputs
- Resource directives
- Profiles and scheduler execution
- Containers
- Cache-aware resumption
- Publishing final outputs

## Debugging checklist

- Print or inspect constructed commands before expensive runs.
- Check that channel shapes match process declarations.
- Confirm whether a task should run per file or once per collection.
- Use unique output locations.
- Resume only when cached tasks remain valid.
- Inspect scheduler state and cancel clearly incorrect expensive runs.
- Separate workflow logic from infrastructure configuration.

Course-specific filesystem paths, allocation identifiers, and container cache locations are deliberately omitted.
