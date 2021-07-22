# EEPs [![Telegram](https://t.me/eos_enhancements_proposals)]
EOS Enchancement Proposals (EEPs) describe standards for the EOSIO platform, including core protocol specifications, client APIs, and contract standards.

# Contributing

 1. Review [EEP-1](EEPS/eep-1.md).
 2. Fork the repository by clicking "Fork" in the top right.
 3. Add your EEP to your fork of the repository. Please follow the format described in [EEP-1](EEPS/eep-1.md) under the 'What belongs in a successful EEP?' section.
 4. Submit a Pull Request to EOSIO's [EEPs repository](https://github.com/EOSIO/EEPs).

Your first PR should be a first draft of the final EEP. It must meet the formatting criteria enforced by the build (largely, correct metadata in the header). An editor will manually review the first PR for a new EEP and assign it a number before merging it. Make sure you include a `discussions-to` header with the URL to a discussion forum or open GitHub issue where people can discuss the EEP as a whole.

If your EEP requires images, the image files should be included in a subdirectory of the `assets` folder for that EEP as follow: `assets/eep-X` (for eep **X**). When linking to an image in the EEP, use relative links such as `../assets/eep-X/image.png`.

Once your first PR is merged, we have a bot that helps out by automatically merging PRs to draft EEPs. For this to work, it has to be able to tell that you own the draft being edited. Make sure that the 'author' line of your EEP contains either your GitHub username or your email address within triangle brackets (ex: < exmaple@email.com >). If you use your email address, that address must be the one publicly shown on [your GitHub profile](https://github.com/settings/profile).

When you believe your EEP is mature and ready to progress past the draft phase, you should open a PR changing the state of your EEP to 'Submitted'. An editor will review your draft, mark it 'Ready for Review', and set an ad-hoc meeting to discuss the proposal. The discussions will determine how the proposal will flow through the EEPs lifecycle. If the editor decides there is no rough consensus - for instance, because contributors point out significant issues with the EEP - they may close the PR and request that you fix the issues in the draft before trying again.

# EEP Status Terms
* **Draft** - the EEP is currently a work in progress and has not yet been submitted
* **Submitted** - the final draft of the EEP has been subitted by an EEP author
* **Ready for Review** - the EEP has been reviewed by an EEP editor and has been added to the agenda for the next EEP review meeting
* **Accepted** - the EEP was analyzed and discussed by the EEP reviewers and has sufficient support for implementation
* **Under Development** - the EEP is currently under developmnet
* **Pending PR Review** -the an EEP implementation is currently being reviewed for final acceptance
* **Final** - the EEP has been successfully implemented and is now active
* **Deferred** - the EEP has been put off for future consideration
* **Living** - this is similar to Final, but denotes an EEP which requires regular updates for accuracy (good for token/wallet standards)
* **Archived** - the EEP is no longer under consideration (withdrawn by author, not enough support for the proposal, etc)
