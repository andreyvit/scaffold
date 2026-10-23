# Production, staging and local dev environments for apps, servers, services

App runs in `production`, `staging`, `testing` and `development` environments. Development is default and appropriate for local work. Override via `-env`/`--env` command-line flag. Environment is just a string.

Environments belong to groups, all are in `all`, more complex apps have `all-local` and `all-production-like`.

Use environment to choose the right configuration and for display/logging. Do not vary behavior by comparing environment names directly.

Unknown environment is fatal crash.

Define available environments in code, e.g.

```go
var Envs = []string{"production", "staging", "testing", "development"}

var EnvGroups = map[string][]string{
	"production": []string{"all", "all-production-like"},
	"staging": []string{"all", "all-production-like"},
	"testing": []string{"all", "all-local"},
	"development": []string{"all", "all-local"},
}
```
