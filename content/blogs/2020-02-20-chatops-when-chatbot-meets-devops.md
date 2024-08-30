---
title: "ChatOps: When ChatBot meets DevOps"
author: Victor Bogo
date: '2020-02-20'
---

*Originally written for [ContAzul's dev blog, in Brazilian Portuguese](https://engineering.contaazul.com/chatops-o-encontro-do-chatbot-com-a-cultura-devops-9c43709dab54)*

Over the past few years, modern software development has undergone significant changes. One of these changes is the drastic increase in traction for agile cultures like DevOps, which aims to bring application operations closer to development. The adoption of this culture, along with the advent of cloud applications, brings numerous benefits, enabling engineering teams to make more frequent and often more complex deliveries.

To achieve this in a healthy and reliable way, practices like process automation, increased collaboration between teams, and observability are crucial for success. Tools like ChatBots greatly support these goals.

## ChatBots

ChatBots were created to provide a user-friendly interface for executing pre-automated actions. They are present in various situations within the tech industry, such as in customer communication through chat. Essentially, these are integrations between chat tools (like Intercom, Slack, and Gitter) and applications capable of interpreting text messages and transforming them into a corresponding outcome, whether to facilitate a conversation, retrieve information, or execute some processing. Below, we have an example of a ChatBot being used to return the reference for each HTTP code:

<img src="/images/chatops-when-chatbot-meets-devops/chatbot.png" alt="Chatbot being used for HTTP requets" width="800"/>

When discussing the internal use of ChatBots, it's easy to see how these tools have great potential to make the execution of actions more efficient. After all, communication tools are already a part of the daily routine of those involved, making access to these functionalities quicker and simpler.

## DevOps and automation

It's hard to think about DevOps without thinking about automation. As one of the main pillars of this culture, the automation of processes and tasks has several advantages, including increased agility and accuracy in execution. The term "ChatOps" emerged when Chatbot tools began to be used as a means of interacting with the execution of automated actions in the DevOps world, whether it's deploying a new version to the production environment or creating a new [Post Mortem](https://landing.google.com/sre/sre-book/chapters/postmortem-culture/).

<img src="/images/chatops-when-chatbot-meets-devops/post-mortem.png" alt="Chatbot being used to create a Post Mortem, in PT-BR" width="800"/></br>

The use of ChatBots to assist in the Post Mortem creation process allows anyone with access to Slack to create a new document in Google Docs based on our template and an epic in [JIRA](https://www.atlassian.com/software/jira) with just a few commands, linking the two entities and setting up all the necessary details. This helps us increase the quality and accuracy of creating well-written and organized Post Mortems.

## ContaAzul's ChatBot architecture

To solve the specific problem of creating a new Post Mortem, we decided to develop a microservice responsible for interpreting an HTTP request and creating the necessary entities in Google Docs and JIRA. For the ChatBot, we used the [Hubot](https://hubot.github.com/) framework created by GitHub to abstract the integrations with Slack (making it easy to switch tools if needed) and to handle the bot's behavior (listening, responding, etc.).

<img src="/images/chatops-when-chatbot-meets-devops/chatbot-architecture.png" alt="Chatbot architecture" width="800"/></br>

With Hubot, you only need to create small scripts in CoffeeScript or JavaScript containing the logic of the conversation (or just a response) as desired. In this example, the script is configured to respond when directly mentioned and to listen to any conversation in the channel. This framework also supports the use of plugins, which are scripts created by third parties and made available through NPM. To find them, just search for [hubot-*](https://www.npmjs.com/search?q=hubot-*).

## Next Steps

Now that we have the tools chosen and provisioned, there are other actions that can be automated for use with the ChatBot. Some of them already on the radar for future implementation are:

- Automating the Incident Response Process to achieve more agility and traceability during incident resolution.
- Fetching crucial information to be used during incident response, such as application response times and the last X releases made.
- Rollout and rollback of versions through chat.

## Wrapping up

Often, increased complexity makes processes more bureaucratic and laborious to maintain a certain level of quality. However, tools and practices like ChatOps allow for leveraging automation to mitigate this impact and bring additional benefits, such as increased accuracy and standardization.

### References

Paperback [ChatOps: Managing Operations in Group Chat](https://www.amazon.com/ChatOps-Managing-Operations-Group-Chat/dp/1491962305)</br>
Shopify Blog: [Implementing ChatOps into our Incident Management Procedure](https://engineering.shopify.com/blogs/engineering/implementing-chatops-into-our-incident-management-procedure)</br>
PagerDuty Blog: [What is ChatOps? And How I Get Started?](https://www.pagerduty.com/blog/what-is-chatops/)</br>
