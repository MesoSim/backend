# backend
Data handling backend for Level II data, warnings, LSRs, and more.

Also includes tools for generating the data archive to replay during a simulation exercise.

## Running the backend

**New way**: Literally just use the run-case script. This, given a case's start and end time, speed up factor, radar site list, and WFO list (along with appropriate staging and target directories), will do everything needed to run a full case. Start this script a bit before you want the case to actually run (to give time to load up warnings and LSRs, as well as).

Since the LSRs are archived through this script, but run through the frontend API, it will reach out to the frontend API to trigger the loading (admin password required)

**Old way**:

1) Get all the case info (start/end times, radar site list, WFO list)
2) Download and unzip all radar files (whether from S3 or NCEI) (this will likely take a while)
3) Run the `archive-lsrs`, `archive-warnings`, and `process-radar` scripts
4) Copy `lsr.db` to the appropriate location
5) Run `simulation-start` when ready to start
6) In separate tmux windows, run `simulation-warning` and `simulation-radar` (to case completion)

## License

Copyright 2020, MesoSim Developers

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

  https://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
