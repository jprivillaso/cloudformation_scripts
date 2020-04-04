# Send an email to a list of recipients when a Codepipeline fails

It's a very common requirement to configure your codepipeline to send emails whenever a pipeline fails.

AWS allows you to trigger an action when a state changes, and allows you to specify which states do you want to listen.

In this specific case, we'll listen only to Failing states at any stage, pipeline or action inside your pipeline. You can customize it by adding or removing items to the `detail-type` configuration, under your `AWS::Events::Rule` resource.

The most important thing to understand is that whenver you create these resources manually, AWS adds the policies to the SNS Topic automatically, but this doesn't happen when using Cloudformation. Thus, it's mandatory to create the policy that allows the Topic to send an email and publis the topic.
