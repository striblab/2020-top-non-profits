# 2019 Top Non Profits

2019 list of top non profits in Minnesota

## Data

Data is manaually managed by Star Tribune through the Data Drop database, and specifically through the Data UI interface. To use this API for building the project, set the following environment variable, optionally in a `.env` file:

- `DATA_UI_URI` (should NOT include trailing slash)
- `DATA_UI_USERNAME`
- `DATA_UI_API_KEY`

## Contact list and survey

In order to create the contact list and other parts, we also need to some other variables around the survey form:

- `SURVEY_URL` Should be something like `https://docs.google.com/forms/d/e/XXXXXXX/`
- `SURVEY_PASS` Defined in the survey
- `BITLY_SHORTENER_API_KEY` Once you create a Bit.ly account, you can get a "Generic Access Token"

To create the contact list, run the following:

```
node nonprofits/contact-list.js
```

Any mail program can work, but so far this has been done with MailChimp.

1. Create a new list using the exported CSV, importing the fields.
1. Create a campaign that uses the fields, specifically the survey URL.

### Follow-up list

We base the follow up list on who has responded to the survey.

1. Export the CSV from the respondent list and save it in `nonprofits/build/` folder (or somehwere that won't get committed to the repo).
1. Re-run the contact list script, passing along where that file is:
   - `node nonprofits/contact-list.js --exclude="nonprofits/build/XXXX.csv"`
   - This will export a new contact list
   - This will also show a copyable list of emails
1. In MailChimp replicate the campaign
   - In MailChimp, you can send to a group of a list by pasting emails, this is the easier way to create a new list to send to.
   - Update campaign email and wording where needed

### Importing

Once all the responses have come in and the responses have been edited in the spreadsheet, run the following to import:

1. Export the CSV from the respondent list and save it in `nonprofits/build/` folder (or somehwere that won't get committed to the repo).
1. `node nonprofits/import.js --responses="nonprofits/build/XXXX.csv"`
   - Use the `--commit` to commit (this will still ask for confirmation)

### For print

1. Output a CSV for print purposes: `node nonprofits/print.js`

## Publishing

See [docs/publishing.md](./docs/publishing.md).

## Application data

See [docs/application-data.md](./docs/application-data.md).

## Development

See [docs/development.md](./docs/development.md).

### Files and directories

See [docs/development.md](./docs/files-directories.md).

### Testing

See [docs/testing.md](./docs/testing.md).

### Code styles

See [docs/code-styles-linting.md](./docs/code-styles-linting.md).

## License

Code is licensed under the MIT license included here. Content (such as images, video, audio, copy) can only be reused with express permission by Star Tribune.

## Generated

Generated by [Star Tribune StribLab generator](https://github.com/striblab/generator-striblab) on 2018-09-27T19:46:27.645Z.