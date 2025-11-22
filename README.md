# Solana
Solana Perpetuals
Introduction
Solana Perpetuals protocol is an open-source implementation of a non-custodial decentralized exchange that supports leveraged trading in a variety of assets.

Quick start
Setup Environment
Clone the repository from https://github.com/solana-labs/perpetuals.git.
Install the latest Solana tools from https://docs.solana.com/cli/install-solana-cli-tools. If you already have Solana tools, run solana-install update to get the latest compatible version.
Install the latest Rust stable from https://rustup.rs/. If you already have Rust, run rustup update to get the latest version.
Install the latest Anchor framework from https://www.anchor-lang.com/docs/installation. If you already have Anchor, run avm update to get the latest version.
Rustfmt is used to format the code. It requires nightly features to be activated:

Install nightly rust toolchain. https://rust-lang.github.io/rustup/installation/index.html#installing-nightly
Execute git config core.hooksPath .githooks to activate pre-commit hooks.
[Optional] Vscode setup
Install rust-analyzer extension
If formatting doesn't work, make sure that rust-analyzer.rustfmt.extraArgs is set to +nightly
Build
First, generate a new key for the program address with solana-keygen new -o <PROG_ID_JSON>. Then replace the existing program ID with the newly generated address in Anchor.toml and programs/perpetuals/src/lib.rs.

Also, ensure the path to your wallet in Anchor.toml is correct. Alternatively, when running Anchor deploy or test commands, you can specify your wallet with --provider.wallet argument. The wallet's pubkey will be set as an upgrade authority upon initial deployment of the program. It is strongly recommended to make upgrade authority a multisig when deploying to the mainnet.

To build the program run anchor build command from the perpetuals directory:

cd perpetuals
anchor build
Test
Integration and unit tests (Rust) can be started as follows:

cargo test-bpf -- --nocapture
Integration tests (Typescript) can be started as follows:

npm install
anchor test -- --features test
By default, integration tests are executed on a local validator, so it won't cost you any SOL.

Deploy
To deploy the program to the devnet and upload the IDL use the following commands:

anchor deploy --provider.cluster devnet --program-keypair <PROG_ID_JSON>
anchor idl init --provider.cluster devnet --filepath ./target/idl/perpetuals.json <PROGRAM ID>
