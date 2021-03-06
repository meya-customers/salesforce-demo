![Meya build](https://github.com/meya-customers/salesforce-demo/workflows/Meya%20build/badge.svg)


# salesforce-demo

Demo Salesforce CRM, Case, Knowledge, and Live Agent integrations.

## Insurance use-case
In this demo, you'll learn how to:
* build an insurance lead generation app using Salesforce and the Orb,
* triage users based on their attributes, like customer status, or the product they're interested in,
* run flows using agent commands,

Video walkthrough:
* [Demo](https://www.loom.com/share/782fbd9d1ce24e748eb284652ac9c675)
* [Code walkthrough](https://www.loom.com/share/6a7c2e7baa9a4567b0c3522343c9f699)

## Setup

```shell script
brew install python@3 libgit2
MEYA_AUTH_TOKEN=your_meya_auth_token
MEYA_APP_ID=app-your_app_id
# you can optionally setup a venv instead as well
python3 -m venv venv  # optional
. venv/bin/activate  # optional
pip3 install --upgrade \
    --extra-index-url https://meya:$MEYA_AUTH_TOKEN@grid.meya.ai/registry/pypi \
    "pygit2>=1.2.1" \
    "meya-sdk>=2.0.0" \
    "meya-cli>=2.0.0"
# auth (if needed)
meya auth add --auth-token $MEYA_AUTH_TOKEN
# connect to existing app
meya connect --app-id $MEYA_APP_ID
```

## Workflow
```shell script 
meya check
meya format
meya test --watch
# to download secrets
meya vault download --file vault.secret.yaml
# if new secrets (after changing the yaml file)
meya vault upload --file vault.secret.yaml
meya push --watch
# for a full rebuild (useful for production deployments)
meya push --force --build-image
```
