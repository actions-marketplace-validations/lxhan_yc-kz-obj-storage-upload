## GitHub Action to upload files to Yandex Cloud Object Storage in KZ region.

> [!IMPORTANT]
> This is a fork of [this action](https://github.com/yc-actions/yc-obj-storage-upload)
> modified to be used only in the Kazakhstan region while original action was primarily focused on the Russian region.

The action uploads files from the given folder to Yandex Cloud Object Storage
using Service Account Key as authorizations method.

**Table of Contents**

<!-- toc -->

- [Usage](#usage)
- [Permissions](#permissions)
- [License Summary](#license-summary)

<!-- tocstop -->

## Usage

```yaml
- name: Upload files to Object Storage
  id: s3-upload
  uses: "lxhan/yc-kz-obj-storage-upload@v2"
  with:
    yc-sa-json-credentials: ${{ secrets.YC_SA_JSON_CREDENTIALS }}
    bucket: ${{ secrets.BUCKET }}
    root: ./src
    include: | 
      *.js
      package.json
    exclude: | 
      **/*.ts
```

`yc-sa-json-credentials` should contain JSON with authorized key for Service
Account. More info in
[Yandex Cloud IAM documentation](https://cloud.yandex.ru/docs/container-registry/operations/authentication#sa-json).

See [action.yml](action.yml) for the full documentation for this action's inputs
and outputs.

## Permissions

To perform this action, it is required that the service account on behalf of
which we are acting has granted the `storage.uploader` role or greater. If you
want to clear bucket before uploading files using `clear: true` option, the
service account should have `storage.editor` role or greater.

## License Summary

This code is made available under the MIT license.
