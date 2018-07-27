# EIPs [![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/ethereum/EIPs?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)
Ethereum Improvement Proposals (EIPs) describe standards for the Ethereum platform, including core protocol specifications, client APIs, and contract standards.

A browsable version of all current and draft EIPs can be found on [the official EIP site](http://eips.ethereum.org/).

# Contributing

 1. Review [EIP-1](EIPS/eip-1.md).
 2. Fork the repository by clicking "Fork" in the top right.
 3. Add your EIP to your fork of the repository. There is a [template EIP here](eip-X.md).
 4. Submit a Pull Request to Ethereum's [EIPs repository](https://github.com/ethereum/EIPs).

Your first PR should be a first draft of the final EIP. It must meet the formatting criteria enforced by the build (largely, correct metadata in the header). An editor will manually review the first PR for a new EIP and assign it a number before merging it. Make sure you include a `discussions-to` header with the URL to a discussion forum or open GitHub issue where people can discuss the EIP as a whole.

If your EIP requires images, the image files should be included in a subdirectory of the `assets` folder for that EIP as follow: `assets/eip-X` (for eip **X**). When linking to an image in the EIP, use relative links such as `../assets/eip-X/image.png`.

Once your first PR is merged, we have a bot that helps out by automatically merging PRs to draft EIPs. For this to work, it has to be able to tell that you own the draft being edited. Make sure that the 'author' line of your EIP contains either your Github username or your email address inside <triangular brackets>. If you use your email address, that address must be the one publicly shown on [your GitHub profile](https://github.com/settings/profile).

When you believe your EIP is mature and ready to progress past the draft phase, you should do one of two things:

 - **For a Standards Track EIP of type Core**, ask to have your issue added to [the agenda of an upcoming All Core Devs meeting](https://github.com/ethereum/pm/issues), where it can be discussed for inclusion in a future hard fork. If implementers agree to include it, the EIP editors will update the state of your EIP to 'Accepted'.
 - **For all other EIPs**, open a PR changing the state of your EIP to 'Final'. An editor will review your draft and ask if anyone objects to its being finalised. If the editor decides there is no rough consensus - for instance, because contributors point out significant issues with the EIP - they may close the PR and request that you fix the issues in the draft before trying again.

# EIP Status Terms
* **Draft** - an EIP that is open for consideration.
* **Accepted** - an EIP that is planned for immediate adoption, i.e. expected to be included in the next hard fork (for Core/Consensus layer EIPs).
* **Final** - an EIP that has been adopted in a previous hard fork (for Core/Consensus layer EIPs).
* **Deferred** - an EIP that is not being considered for immediate adoption. May be reconsidered in the future for a subsequent hard fork.

# Preferred Citation Format

The canonical URL for a EIP that has achieved draft status at any point is at https://eips.ethereum.org/. For example, the canonical URL for ERC-165 is https://eips.ethereum.org/EIPS/eip-165.
