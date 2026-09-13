# Fireflies Meeting Notes · TrueHorizon $211k Deal Part 2 (Project Management)

**Source URL:** https://app.fireflies.ai/view/Anatomy-of-a-211K-Deal-Part-2::01K0AD1H5PG884CZ0TK4HBG15C
**Page title:** Anatomy of a $211K Deal - Part 2 - Meeting recording by Fireflies.ai
**Captured:** 2026-05-23 (TrueHorizon series, King David's $211k deal anatomy gold)

---

## Fireflies AI Meeting Notes

Loading things up...

Record & transcribe your meetings.
Home
Meetings
Meeting Status
Uploads
Integrations
Analytics
Voice Agents
NEW
AI Skills
Team
Upgrade
Settings
More
Anatomy of a $211K Deal - Part 2
Get started with Fireflies
AI FILTERS
Tasks
30
Metrics
151
Date & Time
57
Questions
64
Pricing
5
SENTIMENTS
Neutral
42%
Positive
55%
Negative
3%
SPEAKER TALKTIME
No speakers detected
This meeting is not transcribed yet to show speakers.
View full AI meeting notes
Summaries, action items, and key insights for all your meetings
Login
Anatomy of a $211K Deal - Part 2
Video
Nate Herk
Jul 16 2025, 8:58 PM
English (Global)
AI automation
Project management
Enterprise deployment
Document processing
Value-based pricing
Team scaling
Overview
True Horizon presented a $211K annual deal with a mid-sized insurance company, showcasing AI automation strategies; co-founder Milan Tahliani led the discussion.
The company has grown to 10 full-time employees since January and completed over 20 enterprise and SMB implementations.
The deal structure utilizes an agent-by-agent deployment model, with ongoing development included in the base monthly fee.
Document processing automation incorporates AI-powered data extraction and supports multiple formats, enhancing compliance and efficiency across teams.
A five-phase delivery process was outlined, integrating ClickUp for task management with categories for effective tracking and management of client tasks.
Performance optimization includes parallelization for simultaneous document processing and comprehensive testing protocols to ensure robustness.
A value-based pricing strategy was recommended, with a focus on demonstrating ROI and client cost savings for the $210K engagement.
The hiring strategy emphasizes selecting high-impact performers aligned with the expectation of generating 5-10 times their monthly salary.
The sales process places a strong emphasis on ROI as the key decision factor, with budget discovery facilitated through relationship-building techniques.
Data privacy compliance requirements vary by industry, with SoC2 and ISO 27001 standards recommended for specific client needs, utilizing AWS Bedrock for local model hosting.
Notes
📊 Project Overview & Context (00:36 - 15:08)
True Horizon presentation of part 2 of $211,000 annual deal with mid-sized insurance company
Milan Tahliani co-founder presenting development and deployment strategy for AI automation system
Company grew to 10 full-time employees since January launch, completed 20+ enterprise and SMB implementations
Deal structure involves agent-by-agent deployment model with ongoing development included in base monthly fee
🖥️ Technical Solution Architecture (07:22 - 08:40)
Document processing automation handling regulatory and legal documentation from multiple input formats (CSV, Excel, PDF, API, SQL calls)
Document processing automation can significantly enhance efficiency in handling regulatory and legal documentation by:
Streamlining data extraction from various input formats, such as CSV, Excel, PDF, and APIs, to ensure consistent and accurate data handling.
Implementing automated workflows that route documents to appropriate teams (e.g., compliance, legal) based on predefined business logic, reducing manual intervention and processing time.
Facilitating compliance with regulatory requirements by maintaining detailed logs and audit trails for all document transactions, ensuring transparency and accountability in the processing workflow.
AI-powered data extraction into standardized schemas with dynamic routing to compliance, underwriting, and legal teams based on business logic
Drop zone portal with drag-and-drop interface built by client's technology partner
A/B testing of foundational models for document analysis with comprehensive logging and audit trails for regulatory compliance
Extensibility features allowing clients to dynamically update rules and business logic
📅 Delivery Workflow & Project Management (11:57 - 18:54)
Five-phase delivery process: Kickoff → Architecture & Roadmapping → Development → Delivery & Handoff → Deployment
ClickUp integration for task management and client portals with six task categories: Inbox, Product Backlog, Current Priorities, In Progress, Review, Done
Sprint-based development with 1-2 week cycles including review cycles and capacity planning
Loom video documentation requirement for developers on completed tasks
Automated batch QA using LLM as judge for output validation before production deployment
📈 Scalability & Performance Solutions (27:33 - 30:47)
Parallelization implementation to handle multiple document processing simultaneously, routing to multiple fine-tuned models for specific data types
Performance benchmarking through dev and test environments with comprehensive testing protocols
Cost management for testing absorbed by agency with automated batch QA running hundreds to thousands of test cases
💰 Pricing & Business Model (21:01 - 37:17)
$210,000 annual deal structured as profitable engagement for 10-15 project team deployment
Value-based pricing strategy recommended, focusing on ROI demonstration and client cost savings
Land and expand approach emphasized for AI implementations with natural workflow expansion opportunities
👥 Team Building & Hiring Strategy (42:42 - 44:39)
Hiring benchmark: 5-10x monthly salary return expectation (5k/month engineer should generate 25k/month)
A-player focus for early-stage teams requiring high-impact performers who own outcomes without micromanagement
Hire to buy back time principle for reinvesting in growth activities
🔍 Sales & Discovery Process (32:05 - 51:08)
ROI demonstration identified as primary client decision factor
Budget discovery through relationship building, tools like Crunchbase, and direct questioning after value establishment
AI adoption segmentation: AI adopters vs AI curious clients, with focus on ready-to-move-forward adopters
🔒 Data Privacy & Security (59:17 - 01:01:01)
Industry-dependent requirements with self-hosted local models via AWS Bedrock for enterprises
Data governance implementation with access controls and data isolation
SoC2 and ISO 27001 compliance sufficient for some clients through N8N Cloud plan
Action items
Nathan Herkelman
DM Apify code winners (Michael $50, Glenn $30, Zane $21) in community platform (59:17)
Post meeting recording in community platform (01:01:01)
Follow up with participants who didn't get questions answered for priority in next session (54:14)
Milan Tahliani
Prepare comprehensive AI sales pipeline presentation for next session scheduled July 30th, 4:00pm Eastern (01:01:36)
Rocco Serdar
Drop business partner's username in chat for community connections (45:06)
Michael Carey
Review first session recording for month-by-month deal breakdown details (21:30)
Transcript
N
Nathan Herkelman
00:00
Just give me one sec here while I'm letting everyone in the call and then we'll go ahead and get started. Thanks for your patience. Hope everyone's having a good week. Nothing too crazy going on. All right, thanks for hopping in, everyone. Just give me one more sec. Just letting people in the room and then we'll go ahead and kick off in like 30 seconds here.
I
Israel Liebana de Marcos
00:34
All right.
M
Milan Tahliani
00:35
All right.
N
Nathan Herkelman
00:36
Yeah, we'll go ahead and get started here. I'm sure some more people will be filtering in as we go. Yeah, thanks for hopping in, everyone. This is part two of the anatomy of a $211,000 deal with true Verizon. So great to have you guys here. If you guys were in that first session, you've already met Millen and kind of heard about our background, the way that we kind of came together back in December and then officially launched Horizon with our other co founder, Tyler, who's also here in mid January.
M
Milan Tahliani
01:03
So. Yeah.
N
Nathan Herkelman
01:04
But if this is your first time hopping in, then yeah, welcome. Great to introduce you to Milan. I'm sure he'll give another quick background introduction before he kicks off with this presentation here. But the way that this session is going to work is we will run. I think he's got a presentation prepared that maybe will be 20, 30 minutes, something like that. And then we're just basically going to open it up for the rest of the hour for Q and A. So any questions you guys may have about the sales process, discovery and scoping, even though we kind of covered that last week, or some of the stuff that he talks about today in the presentation, feel free to raise your hand and ask.
N
Nathan Herkelman
01:38
You can see we've got a raise hand function down on the bottom of the screen and that'll put you in the queue. As you can see, Glenn's got his hand raised right now, so that's how it'll work. We could please ask to stick to one question. If you ask a question and then you want to get back in the queue and wait, feel free to do that, but we'll limit it to one question person just so we can keep the questions rolling and. Yeah, we'll go for about an hour then real quick before I hand it over to you, Milan. Glenn, did you have something you wanted to start us off with or were you just getting ready for later?
G
Glenn Marcus
02:09
I'm getting ready for later.
M
Milan Tahliani
02:11
Okay, gotcha.
M
Milan Tahliani
02:12
Gotcha.
N
Nathan Herkelman
02:12
You may have to put your hand back up because I think sometimes when you speak it'll lower it automatically. So.
M
Milan Tahliani
02:16
But. But cool.
N
Nathan Herkelman
02:17
Good to See, you're eager to ask a question. I'll be excited to hear what that is. But also I would say if Milan's okay with it too, during his presentation, if there's something that's particularly interesting, you can, you know, drop a comment in the chat and I'll be moderating as well, so we can make it pretty interactive as well. So if that all sounds good to you guys and Milan, it sounds good to you, I'll hand it over and you can give a quick intro and then we'll just go ahead and get started.
M
Milan Tahliani
02:39
Yeah, 100% sounds good. Well, thanks for setting the stage there, Nate. Glenn. Appreciate, appreciate the eagerness for sure. I would say forgive me guys in general. Just got some popcorn chicken over there, so if you see me taking a bite, honestly haven't had time for lunch, but anyways, yeah, so appreciate everyone for hopping on. Really, really appreciate your time. And you know, one of the biggest priorities for me obviously is just trying to add as much value as possible. So like Nate said, definitely just want to answer, you know, any questions that come up, but kind of as many as possible. And so, yeah, Matteo, we'll definitely get into privacy and security as we get moving here. And so quick, kind of quick introduction again on me.
00:00
/
01:02:13
1×

Continue viewing the meeting

By clicking "Continue", you agree to our Terms of Service, acknowledge Privacy Policy & consent to Fireflies recording and using your voice data to provide Fireflies' services.

Continue with Google
Continue with Microsoft
Why does Fireflies need my calendar access?
SECURED BY 256-BIT AES AND TLS ENCRYPTION