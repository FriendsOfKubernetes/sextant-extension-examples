# Sextant extension examples

Signed releases of the example extensions of [Sextant](https://github.com/FriendsOfKubernetes/sextant), the free Kubernetes desktop client, for its [extension catalog](https://github.com/FriendsOfKubernetes/sextant-extensions).

| Example | What it does | Source |
|---|---|---|
| Hello pods (`sextant.example.hello-page`) | A page that lists pods live, in Sextant's theme | [`sdk/examples/hello-page`](https://github.com/FriendsOfKubernetes/sextant/tree/main/sdk/examples/hello-page) |
| CRD view (`sextant.example.crd-view`) | A details section, a column and an action for a custom resource | [`sdk/examples/crd-view`](https://github.com/FriendsOfKubernetes/sextant/tree/main/sdk/examples/crd-view) |

The source lives in the Sextant repository, next to the SDK it is written with; this repository only builds and publishes it. Each release says which Sextant commit it was built from.

## How a release is made

The **Release an example** workflow (run by hand) does the following:

1. Checks out Sextant at the commit or tag you give.
2. Builds the example with the SDK (`sdk/scripts/build.mjs`) and packs it (`pack.mjs`) into `<id>-<version>.sextant-ext`.
3. Signs the package with the key in the `SEXTANT_EXAMPLES_SIGNING_KEY` secret (`sextant-ext sign`, minisign's format).
4. Checks the signature with the public key in [`keys/sextant-examples.pub`](keys/sextant-examples.pub).
5. Publishes the release `<example>-v<version>` with both files.

The catalog's workflow lists each example's newest such release.

A version that is already released is refused; raise `version` in the example's `sextant-extension.json` in Sextant first.

## License

MIT or Apache License 2.0, as Sextant: [LICENSE-MIT](LICENSE-MIT), [LICENSE-APACHE](LICENSE-APACHE).
