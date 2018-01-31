## Using this role

Generally this role should be wrapped by a [top level playbook for generating application 
config](https://github.com/mesoform/configure-concierge-app) to be built into the image. However, if ran manually, there is a 
`concierge-app.yml` file which can be passed to `ansible-playbook` but many of the required variables and files will need to be set up
 locally.

Primarily the role simply pulls all of your application variables and scripts together to be added to you container and provides a 
`containerpilot.json5` orchestration file and a basic `docker-compose.yml` file. You can find the template which are used to do this 
in the `templates/orchestration` directory and also an example template in `templates/app` if you wanted to process templates to 
dynamically generate application config.

There are no required variables to run this as a stand alone playbook but have a look at the templates at all or the `if defined`
variables to see which ones you may want to set using `ansible-playbook --extra-vars some_key=some_value`.

## Testing
Add a test tag to the tasks you want to test and run `ansible-playbook -vv concierge-app.yml -t test`

However, because it's generally unlikely this role will be used on its own much, and because it is so easy, we recommend
 [testing whilst integrated as a submodule](https://github.com/mesoform/concierge-app-playbook/blob/master/README.md#submodules)

`-----------------------------------------------------------------------------------------------------------------`
Template by [Mesoform Limited](http://www.mesoform.com)