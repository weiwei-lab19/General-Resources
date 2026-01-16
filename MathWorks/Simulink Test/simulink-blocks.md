# Simulink Blocks specific to Simulink Test Library

## Contents
- [Test Sequence Block](#test-sequence-block)
- [Test Assessment Block](#test-assessment-block)


## Test Sequence Block
Define temporal test conditions using a combination of state, transitions, and temporal logic. 


### `et`
- Built-in variable that tracks how long the system has been in the current state.
- Automatically reset to `0` when entering a new step
- Increments with simulation time while in the current step
- units in seconds by default

### `after(n, time_unit)`
- Returns `true` if at least `n` units of time have elapsed since the associated step became active. Otherwise, the operator returns `false`. 
- `time_unit` = `sec` (seconds), `msec` (milliseconds), or `usec` (microseconds)


## Test Assessment Block