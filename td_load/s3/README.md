# Workflow: td_load Example (Amazon S3)

This example workflow ingests data in daily basis, using [Treasure Data's Data Connector for Amazon S3](https://docs.treasuredata.com/articles/data-connector-s3) with [td_load](http://docs.digdag.io/operators.html#td-load-treasure-data-bulk-loading) operator.

The workflow also uses [Secrets](https://docs.treasuredata.com/articles/workflows-secrets) feature, so that you don't have to include your datasource credentials to your workflow files.

# How to Run

First, you can upload the workflow.

    # Upload
    $ td wf push td_load_example

Second, please set datasource credentials by `td wf secrets` command.

    # Set Secrets
    $ td wf secrets --project td_load_example --set s3.endpoint=s3-us-west-1.amazonaws.com
    $ td wf secrets --project td_load_example --set s3.access_key_id=xyzxyzxyzxyz
    $ td wf secrets --project td_load_example --set s3.secret_access_key=xyzxyzxyzxyz

Now you can reference these credentials by `${secret:}` syntax within yml file for `td_load` operator.

- [config/daily_load.yml](config/daily_load.yml)

Now, you can trigger the session manually.

    # Run
    $ td wf start td_load_example daily_load --session now
    
# Next Step

If you have any questions, please contact support@treasure-data.com.
