# Code Quality


## Code Climate

CodeClimate uses static analysis to find places we can improve our code. It will also help to monitor test coverage.


### codeclimate.yml

```
version: "2"

plugins:     
  stylelint:
    enabled: true
  tslint:
    enabled: true
    config: tslint.json
```
<p style="font-size: 1rem">source: <a href="https://docs.codeclimate.com/docs">https://docs.codeclimate.com/docs</a></p>


## Requirements

PRs to your project should be analyzed via CodeClimate and not approved for merging if they are failing.
