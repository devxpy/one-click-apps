## Repo for CapRover One Click Apps

Process:
- Find/create a docker-compose file for the one click app
- Convert yaml file to json
- Copy the content into the one click ap structure. See this for the reference: [wordpress.json](https://github.com/caprover/one-click-apps/blob/master/public/v1/apps/wordpress.json)
- Variables are prefixed with `$$cap`
- There is one special variable called `$$cap_appname` which exists for all oneclick apps
- Variables can be anywhere in the JSON and they will be replaced by what user enters
- Each variable must have `id`, `label`. It may also have `defaultValue`, `validRegex`, `description`.
- Other than `image`, `environment`, `ports`, `volumes`, `depends_on`, other parameters are ignored. Make sure they are not important.
- Instead of image in a service, you can use `dockerfileLines` which is an array of strings.
- Some webapps, use a non-standard HTTP port. For example, Adminer's Docker image uses port 8080. In this case, add `containerHttpPort` to the service. See [adminer.json](https://github.com/caprover/one-click-apps/blob/master/public/v1/apps/adminer.json) for example.


## Test your One Click Apps
After creating your One-Click app json, like [this](https://github.com/caprover/one-click-apps/blob/master/public/v1/apps/adminer.json), you need to test it before creating a Pull Request. Here is how you test it:
- Login to your CapRover dashboard
- Go to apps and click on Create One Click App
- Select the last option from the dropdown list "TEMPLATE"
- Copy and paste your JSON there, and click NEXT.
- Enter values and make sure it's working as expected.
