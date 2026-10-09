# ICT Educational Software Design — Review Draft

Version: 0.1  
Status: Awaiting review  
Language: English  
Chinese version: [简体中文](education-software-design.zh-CN.md)

# 1. Marketing Research

## Current Problems

- Many educational apps still mainly digitise traditional learning materials rather than provide a truly personalised learning experience.
- Learning data is often collected, but students may not receive clear advice on what they should improve next.
- Passive digital learning can reduce engagement. PISA 2022 reported that around 30% of students were distracted by digital devices in most or every mathematics lesson.
- Learning, revision and study planning are often separated across different applications.

## Existing Applications

### Quizlet
- Strength: strong revision tools, flashcards and active recall.
- Limitation: limited subject-specific visualisation.

### Brilliant
- Strength: strong interactive and visual learning.
- Limitation: mainly focused on STEM subjects such as mathematics and programming rather than a complete ICT learning system.

### MyStudyLife
- Strength: strong study planning and academic organisation.
- Limitation: planning is mainly based on schedules and deadlines rather than detailed learning performance.

## Market Gap

Existing apps usually specialise in one part of the learning process.

**Opportunity:** combine visual learning, individual learning analysis and personalised study planning in one application.

# 2. Goals and Objectives

## Goal

To create a personalised ICT learning application that helps students understand difficult concepts and organise their learning more effectively.

## Objectives

### 1. Video-based Learning
- Provide a short selected learning video before each topic.
- Help students gain basic knowledge before further learning.

### 2. 3D and Interactive Visualisation
- Use 3D models and animations to explain abstract concepts.
- Example: 3D computer hardware models and step-by-step programming execution.

### 3. Individual AI Analysis
- Analyse each student's learning performance.
- Identify weak topics, repeated mistakes and areas that need improvement.

### 4. AI-Personalised Study Plan
- Generate a study plan based on learning performance, examination dates and available study time.
- Adjust learning priorities as the student's performance changes.



## 4. Core Feature Design

### 4.1 Videos and Learning Content

Provide videos associated with ICT topics. For theoretical knowledge, combine videos, notes and quizzes to support learning.

Proposal: label each resource with its topic and link it to relevant visualisations and practice. Video sources, licensing, hosting and possible YouTube integration remain open. YouTube was mentioned as an existing learning channel in the discussion, rather than an approved integration.

### 4.2 ICT Concept Visualisation

The emphasis is on building conceptual models through structures, relationships and dynamic processes.

| Domain | Established presentation direction | Learning purpose |
| --- | --- | --- |
| Hardware | Videos and a 3D PC breakdown showing the positions and relationships of the CPU, RAM, SSD and motherboard | Understand computer components and their relationships |
| Programming | Visualise execution line by line, variable changes, loops and the occurrence of errors | Understand execution and debugging |
| Networking | Show packets travelling from a device through a router to a server | Understand transmission paths and processes |
| Database | Visualise tables and relationships | Understand data organisation and relationships between tables |
| Theoretical knowledge | Videos, notes and quizzes | Understand and reinforce fundamental concepts |

This creates a multimodal learning experience: choose teaching methods appropriate to each topic instead of turning every topic into multiple-choice questions.

Proposal: allow students to control the pace of visualisations and provide explanatory text. Specific interactions, programming languages, hardware model detail and network simulation scope remain open.

### 4.3 Practice and Incorrect Answers

Practice checks understanding and supplies data for performance analysis. The system calculates accuracy and identifies weaker topics and incorrect answers. Multiple-choice questions may be one question format, but should not be assumed to be the only learning method across all domains.

Proposal: associate questions with topics, retain answer results and practice timestamps, and link incorrect answers back to relevant learning content. Question formats, scoring rules, question sources and whether to record answer duration remain open.

### 4.4 Performance Analysis

Application code calculates objective metrics from practice records to support planning.

Established metric directions include:

- Accuracy.
- Weaker topics or concepts.
- Incorrect answer records.
- Score changes after further practice.

For example, hypothetical results of Networking 43%, Database 82% and Programming 61% indicate that Networking needs greater attention. These percentages only illustrate prioritisation logic.

Proposal: show question counts and the data time range to avoid treating a small sample as a stable ability assessment. Aggregation methods, weakness thresholds, weighting of recent results and comparisons across difficulty levels remain open.

### 4.5 AI Personalised Study Planning

Planning uses these inputs:

**Quiz results + weaker topics + available study time + examination date → personalised recommendations**

Responsibilities:

| Application code | AI |
| --- | --- |
| Calculate accuracy, identify weaknesses, organise incorrect answers and score changes | Turn structured learning data into understandable, actionable study plans |

AI's core role is to generate planning recommendations from learning data. A standalone chatbot is not an established requirement in this draft.

Proposal: include topics, recommended resources, practice tasks, estimated duration and recommendation reasons in each plan; validate that the total duration does not exceed available study time. Priority rules, handling a missing examination date and AI service selection remain open.

### 4.6 Continuous Adaptive Adjustment

After students follow a plan and practise again, the system analyses their new performance and adjusts subsequent recommendations.

For example, when Networking improves from 45% to 68%, the system may reduce foundational study in that domain and reallocate time according to performance elsewhere. This example does not establish an adjustment threshold.

Target cycle:

**Performance → Recommendation → Learning → New performance → Updated recommendation**

Proposal: retain plan versions and reasons for changes so students can understand adjustments. Update triggers, frequency and rules for manual edits remain open.

## 5. Representative Student Workflow

The following workflow is proposed from the established features; specific screens and ordering require review:

1. The student enters available study time and an examination date.
2. The student completes initial practice and receives performance analysis by topic.
3. The system generates a study plan based on actual practice data.
4. The student follows the plan using videos and relevant concept visualisations.
5. The student completes linked practice and reviews scores and incorrect answers.
6. The system analyses new performance and updates weaker topics and the subsequent plan.

Open questions: whether to use a diagnostic quiz when no practice history exists, and whether students may select a topic and start learning directly.

## 6. Proposed Data and Module Connections

To support the cycle, use shared topic identifiers to connect the following information:

| Information | Purpose |
| --- | --- |
| Topics and domains | Connect content, questions, analysis and plans |
| Videos, notes and visualisation resources | Provide learning entry points for each topic |
| Questions and answer records | Support scoring, incorrect answer review and performance calculations |
| Performance summaries | Inform planning and show changes |
| Study time and examination date | Constrain scheduling |
| Plans and update history | Support task execution and explanations of adjustments |

This is a logical data design proposal. Database schemas, interfaces and the technology stack have not been selected.

## 7. Core Competitive Advantages

1. **A complete learning cycle**: connect understanding, practice, analysis and planning, then adapt using subsequent results.
2. **Performance-based planning**: prioritise study according to students' actual weaker areas.
3. **ICT concept visualisation**: build conceptual models through component relationships, code execution, network flow and table relationships.
4. **AI with a defined role**: generate actionable recommendations from objectively calculated learning data.
5. **Multimodal teaching**: use learning methods appropriate to each domain.
6. **Continuous adaptation to progress**: update recommendations and learning paths as new results become available.

Concise wording for a proposal:

> The competitive advantage of the proposed application lies in integrating multimedia learning, interactive visualisation, performance analysis and AI-powered study planning into one adaptive learning cycle. The app identifies students' actual weaknesses, visualises difficult ICT concepts and continuously adjusts their learning plan according to their progress.

The three main selling points are **ICT concept visualisation, performance-based personalised study planning and a complete adaptive learning cycle**.

These are proposed differentiators. This draft contains no competitor research or learning outcome experiments and therefore does not establish superiority over existing products.

## 8. Proposed Initial Scope and Acceptance Criteria

The initial release should first demonstrate a complete cycle, then expand content coverage. Hardware, Programming, Networking and Database are all part of the product direction; the depth of initial coverage in each domain requires review.

Proposed acceptance criteria:

- A topic connects learning content, visualisation, practice and performance records.
- Practice scores and accuracy can be recalculated from answer records.
- Study plans reference existing performance data and explain why a topic needs attention.
- Scheduled study does not exceed the student's stated available time.
- After further practice, analysis uses the new data and plans update according to approved rules.
- Visualisations correctly represent selected concepts, with understanding questions available to assess their learning objectives.

These are proposed acceptance criteria, rather than completed tests or a fully approved requirement set.

## 9. Review Checklist and Open Decisions

- [ ] Accuracy of the product positioning, core cycle and three main selling points.
- [ ] Target students, ICT curriculum scope and examination system.
- [ ] Initial content coverage and implementation depth of each visualisation type.
- [ ] Platforms, account requirements and whether teacher or administrator roles are needed.
- [ ] Content and question sources, licensing and maintenance ownership.
- [ ] Question formats, scoring, weakness identification and priority calculation rules.
- [ ] Input methods for available study time and examination date.
- [ ] Plan update timing, student editing permissions and behaviour when data is missing.
- [ ] AI service selection, input data scope and generated output validation.
- [ ] Student data storage, access, retention and deletion requirements, including applicable requirements if minors are involved.
- [ ] Technology stack, deployment approach, budget and performance targets.

Review feedback can identify content to retain, modify, remove or add by section. After approval, this draft can be developed into implementation requirements and development tasks.
