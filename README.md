# Citations - How to

## Azure OpenAI - Datasources
When utilizing a data source with Azure OpenAI, citations are included in an attribute named context.

Request
```bash
curl -i -X POST $api_base/openai/deployments/$deployment_id/extensions/chat/completions?api-version=2023-08-01-preview \
  -H "Content-Type: application/json" \
  -H "api-key: $api_key" \
  -d \
'{
  "dataSources": [
    {
      "type": "AzureCognitiveSearch",
      "parameters": {
        "endpoint": "'$search_endpoint'",
        "indexName": "'$search_index'",
        "semanticConfiguration": "standard",
        "queryType": "vectorSemanticHybrid",
        "fieldsMapping": {},
        "inScope": true,
        "roleInformation": "You are an AI assistant that helps people find information.",
        "filter": null,
        "strictness": 3,
        "topNDocuments": 5,
        "key": "'$search_key'",
        "embeddingDeploymentName": "text-embedding-ada-002"
      }
    }
  ],
  "messages": [
    {
      "role": "system",
      "content": "You are an AI assistant that helps people find information."
    },
    {
      "role": "user",
      "content": "Give me deployment options for Azure Functions."
    }
  ],
  "deployment": "gpt-4-32k",
  "temperature": 0,
  "top_p": 1,
  "max_tokens": 800,
  "stop": null,
  "stream": true
}'
```

Response
```json
{
  "id": "17bd56b9-e4be-4503-97da-6f63e95a69d7",
  "model": "gpt-4-32k",
  "created": 1710256105,
  "object": "extensions.chat.completion",
  "choices": [
    {
      "index": 0,
      "finish_reason": "stop",
      "message": {
        "role": "assistant",
        "content": "Azure Functions provides multiple hosting options, allowing you to build once and deploy to multiple destinations. These include various plans such as the Consumption plan, Elastic Premium plan, and Dedicated app service plan. Additionally, Azure Functions can be deployed to Kubernetes or AKS clusters using the open source Azure Functions host images [doc1]. \n\nAzure Functions also supports deployment from code to the cloud using all of the DevOps tooling that Azure Functions supports. For example, you could deploy using GitHub actions or Azure DevOps pipelines. If you have a web app or function app and a backend db, all of them hosted on containers, you could integrate them and deploy at one go using ARM templates or Bicep templates [doc2].\n\nAzure Functions for microservices can be deployed using various tools like AZCLI, Azure Portal, Func Core Tools, GitHub Actions, and AZ DevOps Pipeline tasks [doc4]. \n\nFinally, Azure Functions now has Python 3.10 support in GA, which is useful if you're going to call it from an Azure static web app [doc5].",
        "end_turn": true,
        "context": {
          "messages": [
            {
              "role": "tool",
              "content": "{\"citations\": [{\"content\": \"Microsoft Developer\\nVideo Name: Focus on code not infra with Azure Functions Azure Spring Apps Dapr | BRK221H+\\nYouTube Channel: Microsoft Developer\\nPublish Date: 2023-05-25 00:00:00\\nYouTube-ID: S7NLUH0dnDE \\nTimecode: 00:23:00 \\nText: It provides an edge compute where you could write code in the language of your choice. You can connect to various services using the triggers and bindings that are available out of the box using the Azure Functions extensions, so you need not hard code any integrations to the services. Azure Functions also provides an end to end development experience with both the inner loop and the outer loop experience, so you could code, build, debug, deploy, and monitor your function apps. Azure Functions provides multiple hosting options. You could build once and deploy to multiple destinations. There are several plans that are available in Azure functions, like Consumption plan, Elastic Premium plan, Dedicated app service plan. Or you could deploy Azure Functions to Kubernetes or AKS clusters using the open source Azure Functions host images. Finally, Azure Functions can scale per demand as per the load,\\nFocus on code not infra with Azure Functions Azure Spring Apps Dapr | BRK221H\", \"id\": null, \"title\": null, \"filepath\": null, \"url\": null, \"metadata\": null, \"chunk_id\": \"0\"}, {\"content\": \"Microsoft Developer\\nVideo Name: Focus on code not infra with Azure Functions Azure Spring Apps Dapr | BRK221H+\\nYouTube Channel: Microsoft Developer\\nPublish Date: 2023-05-25 00:00:00\\nYouTube-ID: S7NLUH0dnDE \\nTimecode: 00:25:00 \\nText: Azure Functions already supports that. With Azure Functions for microservices can be deployed from code to the cloud using all of the DevOps tooling that Azure Functions supports. Let's say for example, you could deploy using GitHub actions or Azure DevOps pipelines. Finally, you can easily integrate with other microservice apps. Let's say you have a web app or function app and a backend db, all of them hosted on containers, and you could integrate them and deploy at one goal using ARM templates or Bicep templates. On the other hand, with Dapr you can actually integrate these microservices together and use the best practices with respect to secure connectivity between microservices, or you could even use the features available from Dapr like resiliency and observability. Here the underlying layer is completely managed,\\nFocus on code not infra with Azure Functions Azure Spring Apps Dapr | BRK221H\", \"id\": null, \"title\": null, \"filepath\": null, \"url\": null, \"metadata\": null, \"chunk_id\": \"0\"}, {\"content\": \"Microsoft Developer\\nVideo Name: Focus on code not infra with Azure Functions Azure Spring Apps Dapr | BRK221H+\\nYouTube Channel: Microsoft Developer\\nPublish Date: 2023-05-25 00:00:00\\nYouTube-ID: S7NLUH0dnDE \\nTimecode: 00:24:00 \\nText: and you pay for the compute that's being used. As you can see, the entire underlying layered is being managed, so you need not worry about maintaining the service. I'm super happy to announce the public preview launch of event driven serverless Azure Functions for microservices. This is going to enable you to deploy Azure Functions on this managed micro-services environment easily and quickly. It also has the flexibility to run functions along with other microservices, websites, workflows, or any container hosted programs. You could write the functions code in the language of your choice. You could leverage the triggers and bindings, and it also provides with end to end development experience. In the cloud-native space, the DevOps processes and tools are used to manage the cloud-native apps.\\nFocus on code not infra with Azure Functions Azure Spring Apps Dapr | BRK221H\", \"id\": null, \"title\": null, \"filepath\": null, \"url\": null, \"metadata\": null, \"chunk_id\": \"0\"}, {\"content\": \"Microsoft Developer\\nVideo Name: Focus on code not infra with Azure Functions Azure Spring Apps Dapr | BRK221H+\\nYouTube Channel: Microsoft Developer\\nPublish Date: 2023-05-25 00:00:00\\nYouTube-ID: S7NLUH0dnDE \\nTimecode: 00:31:00 \\nText: Then provide the image, which is the container repository URL, where the image is hosted, and the username and password. Azure Functions for microservices supports both public and private repositories. If it's a private repository, you're expected to provide the credentials. Let me go ahead and execute this. While this is executing, Azure Functions for microservices can be deployed using various tools like AZCLI, Azure Portal, Func Core Tools, GitHub Actions and AZ DevOps Pipeline tasks. Now I'm going to show you how to deploy the function app using Portal. This is the Create Function App experience. I'm going go ahead and get the subscription, and choose a resource group.\\nFocus on code not infra with Azure Functions Azure Spring Apps Dapr | BRK221H\", \"id\": null, \"title\": null, \"filepath\": null, \"url\": null, \"metadata\": null, \"chunk_id\": \"0\"}, {\"content\": \"John Savill's Technical Training\\nVideo Name: Azure Infrastructure Weekly Update - 17th February 2023+\\nYouTube Channel: John Savill's Technical Training\\nPublish Date: 2023-02-17 00:00:00\\nYouTube-ID: fqYfqbRgzjU \\nTimecode: 00:03:00 \\nText: pages could have been created by some other language. But it also has managed functions. So when I do need some server side processing, it can just sort of relative path call one of those managed functions. What was part of it, it will actually go and build that function. And deploy that function for you. So now if that managed function. Is Python, it can be 3.10 and it will still go and get it from the repo, deploy it out to Azure functions and give me that nice relative path I can call for my regular JavaScript for example. And with that. Azure functions now has Python 310 support in GA, which is kind of required if we're going to call it from an Azure static web app. Azure functions are also now has an SDK type binding, so with an Azure function it's event driven, so we have some trigger and then we can have additional bindings for input and output. And before these were always based\\nAzure Infrastructure Weekly Update - 17th February 2023\", \"id\": null, \"title\": null, \"filepath\": null, \"url\": null, \"metadata\": null, \"chunk_id\": \"0\"}], \"intent\": \"[\\\"Overview of deployment options for Azure Functions\\\"]\"}",
              "end_turn": false
            }
          ]
        }
      }
    }
  ],
  "usage": {
    "prompt_tokens": 4546,
    "completion_tokens": 224,
    "total_tokens": 4770
  }
}
```
Learn more: https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/use-your-data?tabs=ai-search

## Semantic Kernel
In Semantic Kernel, citations are integrated from document memories (relevant documents identified through vector search) during the querying process. Below is the relevant code:

Source: https://github.com/microsoft/chat-copilot/blob/8ca758caf17ea140e015cd530ad87d094396ce00/webapi/Plugins/Chat/SemanticMemoryRetriever.cs#L167
```csharp
(IDictionary<string, List<(string, CitationSource)>>, IDictionary<string, CitationSource>) ProcessMemories()
    {
        var memoryMap = new Dictionary<string, List<(string, CitationSource)>>(StringComparer.OrdinalIgnoreCase);
        var citationMap = new Dictionary<string, CitationSource>(StringComparer.OrdinalIgnoreCase);

        foreach (var result in relevantMemories.OrderByDescending(m => m.Memory.Relevance))
        {
            var tokenCount = TokenUtils.TokenCount(result.Memory.Text);
            if (remainingToken - tokenCount > 0)
            {
                if (result.Memory.Tags.TryGetValue(MemoryTags.TagMemory, out var tag) && tag.Count > 0)
                {
                    var memoryName = tag.Single()!;
                    var citationSource = CitationSource.FromSemanticMemoryCitation(
                        result.Citation,
                        result.Memory.Text,
                        result.Memory.Relevance
                    );

                    if (this._memoryNames.Contains(memoryName))
                    {
                        if (!memoryMap.TryGetValue(memoryName, out var memories))
                        {
                            memories = new List<(string, CitationSource)>();
                            memoryMap.Add(memoryName, memories);
                        }

                        memories.Add((result.Memory.Text, citationSource));
                        remainingToken -= tokenCount;
                    }

                    // Only documents will have citations.
                    if (memoryName == this._promptOptions.DocumentMemoryName)
                    {
                        citationMap.TryAdd(result.Citation.Link, citationSource);
                    }
                }
            }
            else
            {
                break;
            }
        }

        return (memoryMap, citationMap);
    }
}
```

![preview](https://github.com/aymenfurter/aiapps-citations/blob/main/chat-copilot.png?raw=true)

## Direct Prompting 

Source: https://github.com/aymenfurter/azure-transcript-search-openai-demo/blob/main/webapi/appsettings.json#L9
```
This is a chat between an intelligent AI bot named Copilot and {{$audience}}. Don't answer any questions yourself. Always reference one or more youtube videos as provided in your sources. Transcription snippets and corresponding IDs from YouTube videos are provided. Always link to a youtubeId and timecode when using the transcript
```
Then, you can review the sources mentioned and cite only the relevant ones. https://github.com/aymenfurter/azure-transcript-search-openai-demo/blob/c70727e47b23968d2aa862a9aaf8f73bd6d7422c/webapi/Plugins/ChatPlugin/ChatPluginUtilities.cs#L64


## Other techniques

### Generation post-processing
Additional inference call to generate the citations in a subsequent step, see: https://python.langchain.com/docs/use_cases/question_answering/citations#retrieval-post-processing

## Function calling
Post-processing of the generation is enhanced through the use of function calls, ensuring a structured response, see: https://python.langchain.com/docs/use_cases/question_answering/citations#function-calling
