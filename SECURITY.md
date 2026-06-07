# Security Policy

Raids and Gear is a Solana-backed game — real value lives on-chain — so we take
disclosure seriously and want to make it easy and safe to report problems. This is the
canonical place to do that.

## TL;DR

- **Found a vulnerability? Email [security@raidsandgear.com](mailto:security@raidsandgear.com)** or open a private
  [GitHub Security Advisory](https://github.com/Raids-and-Gear/issues/security/advisories/new).
- **Do not** open a public issue, post it in Discord, or exploit it on mainnet.
- Test only against **devnet** or a **local validator** — never with third parties' funds.
- Good-faith research under this policy is authorized; we will not pursue legal action (safe harbor, below).

## What's in scope

| Area                  | Examples                                                                                                                                                                                                                                                 |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **On-chain programs** | Unauthorized mint of `$RNG` or loot, mint-authority bypass, draining treasury / founders vault / rewards reserve, theft or permanent freeze of user funds or cNFTs, loot-roll or VRF manipulation, marketplace settlement bugs, leaderboard payout abuse |
| **Backend services**  | Gameplay-proof forgery (minting unearned loot), faucet drain, auth bypass, SSRF, SQL injection, secret/key leakage                                                                                                                                       |
| **Web client**        | XSS / script injection, transaction-tampering or wallet-draining flows, dependency / supply-chain compromise reachable from the app                                                                                                                      |
| **Infra / config**    | Leaked secrets, deploy-pipeline weaknesses, IDOR against API endpoints                                                                                                                                                                                   |

## What's out of scope

- Devnet griefing with no mainnet relevance; missing rate limits with no concrete impact.
- Volumetric DoS / DDoS, brute force, load testing against shared infra.
- Social engineering of staff or community; physical attacks.
- Automated scanner output with no working proof-of-concept; missing "best-practice" headers with no demonstrated impact; self-XSS; clickjacking on non-sensitive pages.
- Issues in **third-party** systems we depend on (RPC providers, Switchboard, Metaplex Bubblegum, hosting, wallet apps) — report to that vendor, and tell us so we can mitigate.
- Anything requiring a compromised user device, rooted wallet, or already-stolen keys.

## How to report

1. Email **[security@raidsandgear.com](mailto:security@raidsandgear.com)**, or file a **private** Security Advisory on this repo.
2. Include a clear description, impact, the affected component, and **reproduction steps or a proof-of-concept** (devnet / localnet only). A devnet transaction signature or failing test is ideal.
3. One vulnerability per report; if a chain of bugs is needed for impact, explain the chain.
4. Please give us a reasonable time to fix before any public disclosure (see Disclosure).

We acknowledge within **2 business days**, give an initial severity assessment within **5 business days**, and keep you updated through the fix.

## Severity

| Severity     | Meaning                                                                                                                                                      |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Critical** | Direct theft / permanent loss of user or protocol funds; unauthorized mint of `$RNG` or loot; mint-authority bypass; draining a vault or the rewards reserve |
| **High**     | Theft of unclaimed yield/loot; temporary freezing of funds; griefing that forces loss of value                                                               |
| **Medium**   | Loot / leaderboard / economy manipulation without direct theft; limited-impact griefing                                                                      |
| **Low**      | Misbehavior with no funds at risk                                                                                                                            |

Off-chain findings map to the same bands by real-world impact (e.g. proof forgery that mints unearned loot is treated as Critical/High).

## Rewards — honest about our stage

**We will never advertise a bounty we cannot pay.** Rewards scale to severity, to the
funds **actually** at risk, and to what the treasury can honestly honor. Raids and Gear
is a small, pre-revenue project currently on **devnet**, where **no real user funds are
at risk** — so today the program is **recognition-first**:

- Public credit in our security hall-of-fame and contributor acknowledgments.
- Swag, and capped `$RNG` game-token grants.
- A **modest, discretionary USDC honorarium** for Critical/High **logic** bugs that would
  have caused fund loss at mainnet. Cash is small and case-by-case at this stage, not a fixed table.

At mainnet we stand up a **funded pool scaled to value-at-risk and sized to what the
treasury can back** — set publicly when we get there, not a headline number we can't
honor. Any cash reward is paid from operational runway / treasury, **never** from the
on-chain rewards reserve (that is player money). Larger payouts may require sanctions
screening / KYC and cannot go to embargoed jurisdictions.

## Rules of engagement

- Test on **devnet or a local validator only** — never mainnet, third-party wallets, or shared infra.
- Access only data that is yours; do not exfiltrate, pivot, or persist. Stop at the minimum needed to prove impact.
- No privacy violations, no DoS, no spam, no social engineering, no physical access.
- Do not publicly disclose or exploit beyond proof-of-concept until we've shipped a fix and agreed on timing.

## Safe harbor

If you make a good-faith effort to follow this policy, we consider your research
**authorized**, will **not pursue or support legal action** against you for it, and will
work with you if a third party does. Unsure whether something is in scope? Ask first at
[security@raidsandgear.com](mailto:security@raidsandgear.com) — we'd much rather answer than get a report about an accidental overstep.

## Disclosure

We practice **coordinated disclosure**. Default fix window is **90 days** from
acknowledgment (shorter for actively-exploited bugs, longer by mutual agreement for
complex on-chain fixes). When the fix ships we co-publish a write-up and credit you (or
keep you anonymous — your call).
