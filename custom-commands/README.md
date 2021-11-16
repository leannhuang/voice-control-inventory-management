# Custom Commands Deployment
Use this folder to deploy smart plug custom commands on your speech studio

## Content
| File             | Description                                                   |
|-------------------------|---------------------------------------------------------------|
| `smart-stock.json`       | The configuration of the smart stock custom commands           |
| `readme.md`     | This readme file   |

## Domain
This Custom Commands application hosts some basic commands to fulfil the turning On/Off the light

## Example sentences
Here are a few examples. Try these or others of your choice:

```
Add three green boxes
Remove two red boxes
```

## Deploy and note down the `Application ID` and `Speech resource key` value

1. Follow the guidance [here](https://github.com/MicrosoftDocs/azure-docs/blob/master/articles/cognitive-services/Speech-Service/quickstart-custom-commands-application.md#go-to-the-speech-studio-for-custom-commands) to import the `smart-stock.json` file

2. Note down the `region` of the resource you created above for further use 
   
     ![region](../docs/images/region-1.png)

3. Try out some voice command 
   1. Select Train at the top of the right pane

        ![speech-train](../docs/images/speech-train.png)

   2. Once training is completed, select Test and try out the following utterances:
        ```
        Add three green boxes
        Remove two red boxes
        ```
   3. Check the respone in the Test window
        ![test-response](../docs/images/test-response.png)

4. Update prediction LUIS resource [here](https://github.com/MicrosoftDocs/azure-docs/blob/master/articles/cognitive-services/Speech-Service/quickstart-custom-commands-application.md#update-prediction-luis-resource)

5. Publish the application [here](https://github.com/MicrosoftDocs/azure-docs/blob/master/articles/cognitive-services/Speech-Service/quickstart-custom-commands-application.md#publish-the-application)

6. Select `Settings` --> `General` to note down the `Application ID` and `Speech resource key` for further useapp
   
    ![app-id](../docs/images/app-id.png)

## Credits and references
- [Create a voice assistant using Custom Commands](https://github.com/MicrosoftDocs/azure-docs/blob/master/articles/cognitive-services/Speech-Service/quickstart-custom-commands-application.md#publish-the-application) 