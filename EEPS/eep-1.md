---
EEP: 1
title: EEP Purpose and Guidelines
status: Active
type: Meta
author: EOSIO
created: 2021-06-08
---

## What is an EEP?

EEP stands for EOSIO Enhancement Proposal. An EEP is a design document providing information to the EOSIO community, or describing a new feature for EOSIO or its processes or environment. The EEP should provide a concise technical specification of the feature and a rationale for the feature. The EEP author is responsible for building consensus within the community and documenting dissenting opinions.

This process is specifically for the EOSIO protocol. Proposals for EOS mainnet are out of scope for EEPs.

## EEP Rationale

We intend for EEPs to be the primary mechanism for proposing new features, for collecting community input on an issue, and for documenting the design decisions that have gone into EOSIO. Because EEPs are maintained as text files in a versioned repository, their revision history is the historical record of the feature proposal.

For EOSIO implementers, EEPs are a convenient way to track the progress of their implementation. Ideally each implementation maintainer would list the EEPs that they have implemented. This will give end users a convenient way to know the current status of a given implementation or library.

## EEP Roles & Responsibilities

Parties involved in the process are you (the champion or EEP author), the EEP editors, and the EEP reviewers.

Role of an EEP champion or author

The role of the champion is to write the EEP using the style and format described below, shepherd the discussions in the appropriate forums, and build community consensus around the idea.

Role of an EEP editor

For each new EEP that comes in, an editor does the following:

Read the EEP to check if it is ready, sound, and complete. The ideas must make technical sense, even if they don’t seem likely to get to final status.

The title should accurately describe the content.

Check the EEP for language (spelling, grammar, sentence structure, etc.), markup (Github flavored Markdown), code style.

If the EEP isn’t ready, the editor will send it back to the author for revision, with specific instructions.

Once the EEP is ready for the repository, the EEP editor will:

Assign an EEP number (generally the PR number or, if preferred by the author, the Issue # if there was discussion in the Issues section of this repository about this EEP)

Merge the corresponding pull request

Send a message back to the EEP author with the next step.

Many EEPs are written and maintained by developers with write access to the EOSIO codebase. The EEP editors monitor EEP changes, and correct any structure, grammar, spelling, or markup mistakes we see.

The editors don’t pass judgment on EEPs. We merely do the administrative & editorial part.

The current EEP editors are:
* Sana Rauf
* Amanda Clark

Role of the EEP reviewers

The EEP reviewers are responsible for reviewing EEP submissions and deciding next steps. Once an EEP has been submitted by an author and reviewed by an EEP editor, it is added to the agenda for the next review meeting.

EEP reviews will be held ad-hoc at the beginning of the EEP launch and a regular cadence will be determined at a later date. The agenda and meeting details, minutes, and recording will be shared publicly (similar to Ethereum's approach). Anyone from the EOSIO community is welcome to participate and provide technical input and feedback on EEP submissions.

## EEP Workflow

Before Submitting An EEP

Vet your idea, this will save you time. Ask the EOSIO community first if an idea is original to avoid wasting time on something that will be rejected based on prior research (searching the Internet does not always do the trick).

It also helps to make sure the idea is applicable to the entire community and not just the author. Just because an idea sounds good to the author does not mean it will work for most people in most areas where EOSIO is used.

Examples of appropriate public forums to gauge interest around your EEP include: the EOS subreddit, the issues section of the EEPs repository, and the EEP Telegram Channel, or the specific mainnet Telegram channels for each EOSIO chain. In particular, the issues section of the EEPs repository is an excellent place to discuss your proposal with the community and start creating more formalized language around your EEP.

Submit an EEP

Navigate to EOSIO’s official EEP repository

Use a pull request to update the status. Please include a link to where people should continue discussing your EEP. The EEP editors will process these requests as per the conditions below.

Once you’ve submitted your EEP, the EEP will have a ‘Submitted’ status.

EEP Review by an EEP Editor
An EEP editor will review the submitted EEP

If the EEP is ready for review at the next EEP review meeting, the EEP editor will merge the EEP into the main repository 

If the editor has feedback, the EEP editor will correspond with the author until the EEP is ready for review

Review new proposals at the EEP review meeting

Once an EEP editor has approved an EEP submission into “Ready for Review” status, it is added to the agenda for the next EEP review meeting

At the EEP review meeting, proposals are reviewed and discussed. There are four possible paths an EEP submission may take at the EEP review meeting:

Deferred: the EEP submission presents a good idea for the future but cannot be accepted immediately; it will be revisited in the future

Accepted: the EEP submission presents a good idea and can begin development immediately

Living: the EEP requires regular updates and will be a living proposal

Archived: either the author retracts their EEP submission or the EEP does not obtain the consensus it needs to be implemented

EEP Next Steps

Based on the next steps decided at the EEP review meeting:
If Deferred, the EEP will be revisited at a future meeting
If Accepted, the EEP is now available for development
If Living, the EEP will be regularly reviewed to ensure accuracy
If Archived, the justification will be recorded and the EEP will no longer be pursued

EEP Happy Path
Once an EEP is accepted, the proposal is available for development. Any interested entity may begin the implementation of the EEP
Once an EEP has been developed, it will go under PR review
Once the PR review has been completed and successfully passed, the EEP will be deployed and achieve a “Final” status

EEP Statuses
Submitted: the first draft has been submitted by an EEP author
Ready for Review: the EEP has been reviewed by an EEP editor and has been added to the agenda for the next EEP review meeting
Accepted: the EEP was analyzed and discussed by the EEP reviewers and has the sufficient support for implementation
Under Development: the EEP is currently under development
Pending PR Review: the EEP implementation is currently being reviewed
Final: the EEP has been successfully implemented and is now active
Deferred: This is for core EEPs that have been put off for a future hard fork
Living: This is similar to Final, but denotes an EEP which requires regular updates for accuracy (good for token/wallet standards)
Archived: An EEP which that is no longer under consideration

## What belongs in a successful EEP?
It is highly recommended that a single EEP contain a single key proposal or new idea. The more focused the EEP, the more successful it tends to be. A change to one client doesn’t require an EEP; a change that affects multiple clients, or defines a standard for multiple apps to use, does.

An EEP must meet certain minimum criteria. It must be a clear and complete description of the proposed enhancement. The enhancement must represent a net improvement. The proposed implementation, if applicable, must be solid and must not complicate the protocol unduly.
Each EEP should have the following parts:
Preamble: RFC 822 style headers containing metadata about the EEP, including the EEP number, a short descriptive title (limited to a maximum of 44 characters), and the author details. See below for details.
Simple Summary: “If you can’t explain it simply, you don’t understand it well enough.” Provide a simplified and layman-accessible explanation of the EEP.
Abstract: a short (~200 word) description of the technical issue being addressed.
Motivation (*optional): The motivation is critical for EEPs that want to change the EOSIO protocol. It should clearly explain why the existing protocol specification is inadequate to address the problem that the EEP solves. EEP submissions without sufficient motivation may be rejected outright.
Specification: The technical specification should describe the syntax and semantics of any new feature. The specification should be detailed enough to allow competing, interoperable implementations for any of the current EOSIO platforms (eos-go, eosjs)
Rationale: The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.
Backwards Compatibility: All EEPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their severity. The EEP must explain how the author proposes to deal with these incompatibilities. EEP submissions without a sufficient backwards compatibility treatise may be rejected outright.
Test Cases: Test cases for an implementation are mandatory for EEPs that are affecting consensus changes. Other EEPs can choose to include links to test cases if applicable.
Implementations: The implementations must be completed before any EEP is given status “Final”, but it need not be completed before the EEP is merged as draft. While there is merit to the approach of reaching consensus on the specification and rationale before writing code, the principle of “rough consensus and running code” is still useful when it comes to resolving many discussions of API details.
Security Considerations: Discuss the security implications/considerations relevant to the proposed change. Include information that might be important for security discussions, surfaces risks and can be used throughout the life cycle of the proposal.
Intellectual Property: All EEPs submissions must contain the following text: “I hereby agree that this EEP is subject to this copyright waiver and I certify that I have all necessary rights and permissions to make this submission and to agree to such waiver.”

## EEP Types
There are three types of EEP:

- A **Standard Track EEP** describes any change that affects most or all EOSIO implementations, such as a change to the the network protocol, a change in block or transaction validity rules, proposed application standards/conventions, or any change or addition that affects the interoperability of applications using EOSIO. Furthermore Standard EEPs can be broken down into the following categories. Standards Track EEPs consist of three parts, a design document, implementation, and finally if warranted an update to the formal specification.

  - **Core** - improvements requiring a consensus fork, as well as changes that are not necessarily consensus critical but may be relevant to Block Producer and EOSIO discussions 

  - **Networking** - improvements around p2p protocol

  - **Interface** - includes improvements around client API specifications and standards, and also certain language-level standards like contract ABIs. For contract ABIs, it aligns with the [eosio.contracts repo](https://github.com/EOSIO/eosio.contracts) and discussion should primarily occur in that repository before an EEP is submitted to the EEPs repository
  
- An **Informational EEP** describes an EOSIO design issue, or provides general guidelines or information to the EOSIO community, but does not propose a new feature. Informational EEPs do not necessarily represent EOSIO community consensus or a recommendation, so users and implementers are free to ignore Informational EEPs or follow their advice.

- A **Meta EEP** describes a process surrounding EOSIO or proposes a change to (or an event in) a process. Process EEPs are like Standard Track EEPs but apply to areas other than the EOSIO protocol itself. They may propose an implementation, but not to EOSIO's codebase; they often require community consensus; unlike Informational EEPs, they are more than recommendations, and users are typically not free to ignore them. Examples include procedures, guidelines, changes to the decision-making process, and changes to the tools or environment used in EOSIO development. Any meta-EEP is also considered a Process EEP.

## EEP Formats and Templates

EEPs should be written in [markdown] format.
Image files should be included in a subdirectory of the `assets` folder for that EEP as follow: `assets/eep-X` (for eep **X**). When linking to an image in the EEP, use relative links such as `../assets/eep-X/image.png`.

## EEP Header Preamble

Each EEP must begin with an RFC 822 style header preamble, preceded and followed by three hyphens (`---`). The headers must appear in the following order. Headers marked with "*" are optional and are described below. All other headers are required.

` eep:` <EEP number> (this is determined by the EEP editor)

` title:` <EEP title>

` author:` <a list of the author's or authors' name(s) and/or username(s), or name(s) and email(s). Details are below.>

` * discussions-to:` <url>

` status:` <Draft | Last Call | Accepted | Final | Active | Deferred | Rejected | Superseded>

`* review-period-end: YYYY-MM-DD

` type: `<Standards Track (Core, Networking, Interface) | Informational | Meta>

` * category:` <Core | Networking | Interface > 

` created:` <date created on, in ISO 8601 (yyyy-mm-dd) format>

` * requires:` <EEP number(s)>

` * replaces:` <EEP number(s)>

` * superseded-by:` <EEP number(s)>

` * resolution:` <url>

#### Author header

The author header optionally lists the names, email addresses or usernames of the authors/owners of the EEP. Those who prefer anonymity may use a username only, or a first name and a username. The format of the author header value must be:

Random J. User &lt;address@dom.ain&gt;

or

Random J. User (@username)

if the email address or GitHub username is included, and

Random J. User

if the email address is not given.

Note: The resolution header is required for Standards Track EEPs only. It contains a URL that should point to an email message or other web resource where the pronouncement about the EEP is made.

While an EEP is a draft, a discussions-to header will indicate the mailing list or URL where the EEP is being discussed. As mentioned above, examples for places to discuss your EEP include [EEPs Channel on Telegram](https://t.me/eos_enhancements_proposals), an issue in this repo or in a fork of this repo, the [EOS Mainnet BPs Telegram Channel](https://t.me/joinchat/HbgyfEqlPd_HCo4R8EJsnw) (as well as other EOSIO mainnet channels) and [Reddit r/eos](https://www.reddit.com/r/eos/). No discussions-to header is necessary if the EEP is being discussed privately with the author.

The type header specifies the type of EEP: Standards Track, Meta, or Informational. If the track is Standards please include the subcategory (core, networking, interface, or RFC). 

The category header specifies the EEP's category. This is required for standards-track EEPs only.

The created header records the date that the EEP was assigned a number. Both headers should be in yyyy-mm-dd format, e.g. 2001-08-14.

EEPs may have a requires header, indicating the EEP numbers that this EEP depends on.

EEPs may also have a superseded-by header indicating that an EEP has been rendered obsolete by a later document; the value is the number of the EEP that replaces the current document. The newer EEP must have a Replaces header containing the number of the EEP that it rendered obsolete.

Headers that permit lists must separate elements with commas.

## Auxiliary Files

EEPs may include auxiliary files such as diagrams. Such files must be named EEP-XXXX-Y.ext, where “XXXX” is the EEP number, “Y” is a serial number (starting at 1), and “ext” is replaced by the actual file extension (e.g. “png”).

## Transferring EEP Ownership

It occasionally becomes necessary to transfer ownership of EEPs to a new champion. In general, we’d like to retain the original author as a co-author of the transferred EEP, but that’s not always possible or may not be the preference of the original author. A good reason to transfer ownership is because the original author no longer has the time or interest in updating it or following through with the EEP process, or has fallen off the face of the ‘net (i.e. is unreachable or isn’t responding to email). A bad reason to transfer ownership is because you don’t agree with the direction of the EEP. We try to build consensus around an EEP, but if that’s not possible, you can always submit a competing EEP.

If you are interested in assuming ownership of an EEP, send a message asking to take over, addressed to both the original author and the EEP editor. If the original author doesn’t respond to email in a timely manner, the EEP editor will make a unilateral decision (it’s not like such decisions can’t be reversed).

## History

This document was derived heavily from [Ethereum’s EIP-1] written by Martin Becze, Hudson Jameson, and others, which was derived from [Bitcoin’s BIP-0001] written by Amir Taaki which in turn was derived from [Python’s PEP-0001]. In many places text was simply copied and modified. Although the PEP-0001 text was written by Barry Warsaw, Jeremy Hylton, and David Goodger, they are not responsible for its use in the EOSIO Enhancement Process, and should not be bothered with technical questions specific to EOSIO or the EEP. Please direct all comments to the EEP editors.

## Legal

By participating in the EEP process you agree to terms set forth in this document. If you do not agree to these terms, you may not participate in the EEP process.

Conduct
While participating in this process, please be respectful and constructive, so that participation in our project is a positive experience for everyone.

Examples of behavior that contributes to creating a positive environment include:
Using welcoming and inclusive language
Being respectful of differing viewpoints and experiences
Gracefully accepting constructive criticism
Focusing on what is best for the community
Showing empathy towards other community members

Examples of unacceptable behavior include:
The use of sexualized language or imagery and unwelcome sexual attention or advances
Trolling, insulting/derogatory comments, and personal or political attacks
Public or private harassment
Publishing others’ private information, such as a physical or electronic address, without explicit permission
Other conduct which could reasonably be considered inappropriate in a professional setting

Confidentiality: All EEPs, editor feedback on EEPs and EEPs reivew meeting discussions or feedback on EEPs are considered non-confidential information and may be disclosed to third parties.  This could lead to a third party developing an idea, concept, design or standard described in your EEP without your permission or involvement.
Additional Requirements
  
By participating in the EEP process, you certify that:
You are not, are not acting on behalf of another party that is, and no party with a beneficial interest in you is: 
subject to sanctions administered or enforced by any country or government or otherwise designated on any list of prohibited or restricted parties (including but not limited to the lists maintained by the United Nations Security Council, the U.S. Government, the European Union or its Member States, or other applicable government authority)(“Sanctions”); or
organized or resident in a country or territory that is the subject of country-wide or territory-wide Sanctions
And you acknowledge and agree that:

All EEPs, editor feedback on EEPs and EEP review meeting discussions or written feedback on EEPs are subject to this copyright waiver.

The EEP process does not create an obligation to consider, develop or implement any idea, design, concept or standard that you include in an EEP

The EEP process, including but not limited to EEP editing and EEP reviewer feedback is provided without warranty, guarantee or undertaking of any kind, whether express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose and noninfringement. 

  
In no event shall an EEP editor, an EEP reviewer or Bullish Global or its affiliates (“EEP Participants”) be liable for any claim, damages or other liability, whether in an action of contract, tort or otherwise, arising from, out of or in connection with the EEP process and you waive any claim that you may have against such parties related to their participation in the EEP process 

  
You will not make EEP materials available to any person or entity that is the subject of Sanctions or organized or resident in a country or territory that is the subject of country-wide or territory-wide Sanctions.  You will comply with all applicable import, re-import, sanctions, anti-boycott, export, and re-export control laws and regulations.  If this is not accurate or you do not agree, then you must immediately cease accessing the EEP materials and delete all copies thereof.

Any reference to any third party or third-party product, resource or service is not an endorsement or recommendation by an EEP Participant. EEP Participants are not responsible for, and disclaim any and all responsibility and liability for, your use of or reliance on any of these resources.

Forward Looking Statements

When an EEP Participant makes statements expressing its vision, it does not guarantee anything, and all aspects of its vision are subject to change at any time and at such participant’s sole discretion, with or without notice. We call these “forward-looking statements”, which includes statements on an EEP Participant’s website and in other materials, such as statements regarding EOSIO’s development, expected performance, and future features, or business strategy, plans, prospects, developments and objectives. These statements are based on assumptions and are subject to risk, uncertainties and change at any time.

EEP Participants operate in a rapidly changing environment and new risks emerge from time to time. Given these risks and uncertainties, you are cautioned not to rely on these forward-looking statements. Actual results, performance or events may differ materially from what is predicted in the forward-looking statements. Some of the factors that could cause actual results, performance or events to differ materially from the forward looking statements include, without limitation: technical feasibility and barriers; market trends and volatility; continued availability of capital, financing and personnel; product acceptance; the commercial success of any new products or technologies; competition; government regulation and laws; and general economic, market or business conditions.

  
All statements are valid only as of the date of first posting and EEP Participants are not under and expressly disclaim any obligation to update or alter any statements, whether as a result of new information, subsequent events or otherwise. Nothing provided in the EEP process constitutes technological, financial, investment, legal or other advice, either in general or with regard to any particular situation or implementation. Please consult with experts in appropriate areas before implementing or utilizing any content, guidance or feedback received as part of the EEP process.
Trademarks: EOSIO, EOS, the heptahedron and associated logos and related marks are Bullish Global’s trademarks.

## Bibliography

[eosio.contracts](https://github.com/EOSIO/eosio.contracts)
  
[the EOS subreddit](https://www.reddit.com/r/eos/)
  
[EEP Telegram Channel](https://t.me/eos_enhancements_proposals)
  
[pull request] https://github.com/eoscanada/EEPs/pulls
  
[the Issues section of this repository] https://github.com/eoscanada/EEPs/issues
  
[markdown] https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
  
[Ethereum's EIP-1] https://github.com/ethereum/EIPs/
  
[Bitcoin's BIP-0001] https://github.com/bitcoin/bips
  
[Python's PEP-0001] https://www.python.org/dev/peps/
