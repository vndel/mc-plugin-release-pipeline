# mc-plugin-release-pipeline

Release engineering templates for Minecraft plugins. Produces traceable artifacts from tagged source without embedding credentials in build logs.

## Pipeline contract
- Validate the requested tag and working tree before packaging.
- Run the project's verification command before publishing.
- Generate checksums alongside jars and attach both to a GitHub release.
- Pin third-party actions to reviewed immutable references in production.

## Local release checklist
```sh
git diff --check
mvn -B verify
sha256sum target/*.jar
```

Configure `contents: write` only on the publishing job, keep build jobs read-only, and require protected release tags. No performance claim is made without a reproducible workload. MIT licensed.
