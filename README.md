# JFrog Artifactory

Adding the Account Integration.

You will need to configure this integration to store credentials to artifactory.

 1. Click on the gear icon for Account Settings in your top navigation bar and then click on the 'Integrations' section.
 2. Click on the `Add Integration` button.
 3. For 'Integration type', choose `JFrog Artifactory` from the list of dropdown choices.
 4. For 'Integration Name' use a distinctive name that's easy to associate to the integration and recall. Example: `jfrog-integration`
 5. Enter your HTTP Endpoint(url), API key, username. You can follow instructions in [JFrogCLI-Authentication](https://www.jfrog.com/confluence/display/RTF/JFrog+CLI#JFrogCLI-Authentication)
 6. Click on `Save`

![JFrog_Integration](https://github.com/deepikasl/JFrog_Artifactory/blob/master/images/jfrog-int.png)

## CI

The integration will now be available to all your continuous integration.

### Add the JFrog Artifactory integration to your subscription.
To add ECR integration to your subscription, do the following:

1. Select your Subscription from the dropdown burger bar menu on the top left.
2. Click the 'Settings' tab and go to the 'Integrations' section.
3. Click the Add Integration button.
4. Provide an easy-to-remember name for the Jfrog Artifactory integration for your Subscription, such as `jfrog-integration`, in the 'Name' field. IMPORTANT: The 'Name' you have entered in this step should be used in your `shippable.yml` file. Both names should be exactly the same. If not the build will fail with an error.
5. From the 'Account Integrations' dropdown select the JFrog Artifactory account integration created.
6. Click the `Save` button.
7. The JFrog Artifactory integration will show up in the list of integrations for your subscription.

Here's an example , for reference to configure JFrog Artifactory integration in `shippable.yml`.

```
integrations:
  hub:
    - integrationName: jfrog-integration
      type: artifactory
```

### Upload a file to your Artifactory

 Configure your `shippable.yml` to associate the JFrog integration for your project as part of CI.
 
 In the following example, It is done in `pre_ci` section of `shippable.yml`.
 
 Upload a file called `sample_file.tgz` to the root of the `sample_project` repository of JFrog Artifactory:
 
 ```
 build:
  pre_ci:
    - jfrog rt u sample_file.tgz sample_project
 ```
 
### Download a file from your Artifactory
 
 Configure your `shippable.yml` to associate the JFrog integration for your project as part of CI.
 
 Download an artifact called `sample_file.zip` located at the root of the `sample_project` repository to the current directory.

 ```
 build:
  pre_ci:
    - jfrog rt dl sample_project/sample_file.zip
 ```
Here is [JFrog CLI User guide](https://www.jfrog.com/confluence/display/RTF/JFrog+CLI) for reference.
 

## Deleting the Integration
 
 To remove the JFrog Artifactory integration, you'll need to remove this integration from all dependencies configured to use it. To find all the dependencies:
 
 1. Click on the gear icon for Account Settings in your top navigation bar and then click on the `Integrations` section.
 2. Select the JFrog Artifactory integration from the list of integrations. If you have many entries, use the Filters dropdown and select JFrog Artifactory. Alternatively, you can use the Integration Name field to provide the name of your JFrog integration.
 3. Your JFrog integration shows up in the list.
 4. Click on the `Delete` button.
 5. A window pops up confirming that you want to delete the integration. This window lists all dependencies of this this integration. The list will include any Subscription dependent on this integration.
 6. If there are dependencies, individually access the Settings tab for each Subscription and delete the JFrog Artifactory integration.
 7. Once all dependencies of the JFrog Artifactory integration have been removed, Step 5 will show the message: `No dependency`.
 8. Click the Yes button to delete the JFrog Artifactory Integration.
