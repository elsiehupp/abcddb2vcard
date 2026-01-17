# abcddb2vcard

This python script reads an AddressBook database file (`AddressBook-v22.abcddb`) and export its content to a vCard file (`.vcf`).

I created this script to automate my contacts backup procedure. The output of this script should be exactly the same as dragging and dropping the "All Contacts" card.

## Installation

To install `abcddb2vcard` from [PyPi](https://pypi.org/project/abcddb2vcard/), use `pip`:

```sh
pip install abcddb2vcard
```

Or

```sh
pip3 install abcddb2vcard
```

`abcddb2vcard` can then be used from any working directory in the Terminal.

To uninstall:

```sh
pip uninstall abcddb2vcard
```

Or

```sh
pip3 uninstall abcddb2vcard
```

## Usage

```sh
abcddb2vcard backup/contacts_$(date +"%Y-%m-%d").vcf
```

> assuming db is located at "~/Library/Application Support/AddressBook/AddressBook-v22.abcddb"

### Export into individual files

```sh
abcddb2vcard outdir -s 'path/%{fullname}.vcf'
```

### Extract contact images

```sh
vcard2img AllContacts.vcf ./profile_pics/
```

## Supported data fields

- `firstname`
- `lastname`
- `middlename`
- `nameprefix`
- `namesuffix`
- `nickname`
- `maidenname`
- `phonetic_firstname`
- `phonetic_middlename`
- `phonetic_lastname`
- `phonetic_organization`
- `organization`
- `department`
- `jobtitle`
- `birthday`
- `[email]`
- `[phone]`
- `[address]`
- `[socialprofile]`
- `note`
- `[url]`
- `[xmpp-service]`
- `image`
- `iscompany`

## Limitations

The `image` field currently only supports JPG images. But as far as I see, Apple converts PNG to JPG before storing the image. If you encounter a db which includes other image types, please let me know.

## Disclaimer

You should check the output for yourself before using it in a production environment. I have tested the script with many arbitrary fields, however there may be some edge cases missing. Feel free to create an issue for missing or wrong field values.

> **Note:** The output of `diff` or `FileMerge.app` can be different to this output. Apple does some weird transformations on vcf export that are not only unnecessary but in many cases break the re-import of the file.
