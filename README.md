
This is a workflow repository powered by [Actionsflow](https://github.com/actionsflow/actionsflow), generated from [actionsflow/actionsflow-workflow-default](https://github.com/actionsflow/actionsflow-workflow-default)

# 🏁 Getting Started <a name = "getting_started"></a>

Build an Actionsflow workflow:

1. **Uncomment [`.github/workflows/actionsflow.yml`](/.github/workflows/actionsflow.yml) schedule event**

    ```yml
    on:
      schedule:
        - cron: "*/15 * * * *"
    ```
    > Note: To prevent abuse, by default, the schedule is commented, please modify the schedule time according to your own needs, the default is once every 15 minutes. Learn more about schedule event, please see [here](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#schedule)

1. **Define your [workflow file](https://actionsflow.github.io/docs/workflow/) at `workflows` directory**

   A typical workflow file `rss.yml` looks like this:

   ```yaml
   on:
     rss:
       url: https://hnrss.org/newest?points=300&count=3
   jobs:
     request:
       name: Make a HTTP Request
       runs-on: ubuntu-latest
       steps:
         - name: Make a HTTP Request
           uses: actionsflow/axios@v1
           with:
             url: https://hookb.in/VGPzxoWbdjtE22bwznzE
             method: POST
             body: |
               {
                 "link":"${{ on.rss.outputs.link }}", 
                 "title": "${{ on.rss.outputs.title }}",
                 "content":"<<<${{ on.rss.outputs.contentSnippet }}>>>"
               }
   ```

   For more information about the Actionsflow workflow file, see the
   [Actionsflow workflow reference](https://actionsflow.github.io/docs/workflow/).

   You can explore [Triggers List](https://actionsflow.github.io/docs/triggers/) or [Awesome Actionsflow Workflows](https://github.com/actionsflow/awesome-actionsflow) to get more inspired.

1. **Commit and push your updates to Github**

Then, Actionsflow will run your workflows as you defined, you can view logs at your repository actions tab at [Github](https://github.com)

For more information, see [Full documentation](https://actionsflow.github.io/docs/)

# 🎓 Learn More <a name="reference"></a>

Full documentation for Actionsflow lives [on the website](https://actionsflow.github.io/docs/).

- [Workflow Syntax for Actionsflow](https://actionsflow.github.io/docs/workflow/) - Learn more about the Actionsflow workflow file syntax
- [Triggers List](https://actionsflow.github.io/docs/triggers/) - Explore Actionsflow triggers
- [Awesome Actionsflow Workflows](https://github.com/actionsflow/awesome-actionsflow) - Explore Actionsflow workflows use case to get inspired
- [Core Concepts](https://actionsflow.github.io/docs/concepts/) - Learn more about how Actionsflow worked
- [Creating Triggers for Actionsflow](https://actionsflow.github.io/docs/creating-triggers/) - Learn more about how to create your own trigger for Actionsflow
- [FAQs](https://actionsflow.github.io/docs/faqs/) - Actionsflow FAQs
- [Upgrade Guide](https://actionsflow.github.io/docs/upgrade/)
