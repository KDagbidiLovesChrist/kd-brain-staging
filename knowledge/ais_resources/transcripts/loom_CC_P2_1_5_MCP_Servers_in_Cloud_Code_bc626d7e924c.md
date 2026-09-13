# Loom Transcript · CC_P2_1.5_MCP_Servers_in_Cloud_Code

**Source video ID:** bc626d7e924c45938f4ccc1fa5b25989
**Loom URL:** https://www.loom.com/share/bc626d7e924c45938f4ccc1fa5b25989
**Detected language:** en (probability 1.00)
**Duration:** 229.3s

---

[00:00] Let's talk about MCP servers now and how to use MCP servers within an agentic workflow.
[00:05] In the previous phase in phase one, you install the NADN MCP server to connect Cloud Cloud to your
[00:11] NADN workflows. In this video, we're going to go way deeper, we're going to explain what MCP really
[00:16] is, how to find and install MCP servers for different use cases and when to use MCP versus when to use
[00:23] regular tools. So what is MCP? MCP stands for model context protocol and I know that it may sound a
[00:30] bit techy, but it's actually very simple. Let's think about Gmail. Within Gmail, you can have an
[00:35] action to send an email, an action to draft an email, or an action to get emails. You can see that
[00:41] there are tons of different tools within that one tool. What MCP does, basically it says the agents
[00:47] can figure out how to use all the tools, when to use them and what parameters to use.
[00:52] So the agent and the MCP server are going to connect and the agents now going to be able to know
[00:57] all the tools available and when to call each one and it's going to be able to make its own decisions.
[01:02] So what are we going to do now? To test an MCP server, we're going to install FireCrawl,
[01:08] which is going to give Cloud Code web browsing and scraping capabilities and here we have a guide on
[01:13] how to do it step by step. Step number one, we need to find the Cloud Code section in FireCrawls
[01:19] documentation. We go to FireCrawl, Integrations, MCP, Cloud Code, we're going to scroll down until
[01:27] we find the MCP command. Here it is. We're going to copy this. We're going to go to Visual Studio.
[01:34] We're going to start a new project. I created a new project and called it MCP Intro. I'm going to
[01:40] open Cloud Code. I'm going to close this and I'm going to start a Cloud I want to install
[01:48] FireCrawl MCP server. Use this command and hit Enter. And when it's done working, we're going to see
[02:00] that it created a new file, the MCP Jason, which is going to have the FireCrawl MCP and a placeholder
[02:07] for API key. So all we need to do now is go to FireCrawl, sign up or login and get our API key
[02:14] for our account and paste it here. And that's how easy you can install MCP servers into Cloud Code.
[02:20] Just say, hey, Cloud, I want to install this MCP server for this product, give it the command from
[02:26] their website and Cloud Code is going to do everything for you. All we have to do left is just update the
[02:31] API key, which I recommend that you do it manually. I do not recommend that you add it here and ask
[02:36] Cloud to update it. It's safer if you just add it here manually into this file. And how can we
[02:41] know which MCP servers we have installed in Cloud Code? We can go here slash MCP, MCP status,
[02:49] and it's going to show us all the MCP servers running. And at the bottom, we can see the FireCrawl
[02:54] MCP server. If you're not able to see your latest MCP, you may need to restart either Cloud Code
[03:00] or Visual Studio. Okay, and how can we know where to find different MCP servers based on what we
[03:06] need? We can either go to mcp.so and we'll find a directory of all the existing MCP servers
[03:13] or you could go to GitHub and within GitHub search for MCP server plus whatever the name of the
[03:19] service that you need is. Some popular MCP servers to know about for web scraping, for example,
[03:25] which is use FireCrawl. For databases, we have Postgres and SuperBase. For documents,
[03:32] you could find Google Drive MCP or Notions MCP. And for communications, you could also use
[03:38] Slack or Gmail MCP. And that's it. That's how easy you install MCP servers into Cloud Code.
[03:44] In the next video, we're going to see a full example with FireCrawl and an agentic workflow.
