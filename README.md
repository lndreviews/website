# LND Review Club

This was a fork from https://github.com/bitcoin-core-review-club/website.
Thanks to all the work!

Simple Jekyll site for hosting the LND PR Review club at https://lnd.reviews/.

## Development

You'll need [Ruby and Jekyll](https://jekyllrb.com/docs/installation/) to run
the site locally. Ruby 2.6 is recommended. Once they are set up:

* Clone the repository and go into the directory
* Run `bundle install`
* Run `make preview`
* Go to http://localhost:4000

In case of any issues, don't hesitate to run the following to update rubygems,
bundler, and dependencies: `gem update --system && gem update && bundle update`

## Making a new post

See the [CONTRIBUTING.md](CONTRIBUTING.md) doc for how to create a post for an upcoming meeting.

Quick reference using docker container:
```bash
PR_NUM=<pr_number>
PR_HOST=<github_username>
PR_DATE=<yyyy-mm-dd_review_session_date>

docker build -t lndreviews:dev .
docker run -it --name lndreviews -v $(pwd):/lndreviews lndreviews:dev \
  rake posts:new -- -p $PR_NUM -h $PR_HOST -d $PR_DATE

docker run -it --rm --name lndreviews \
  -v $(pwd):/lndreviews \
  -e PR_NUM -e REVIEW_HOST -e REVIEW_DATE_yyyy-mm-dd \
  lndreviews:dev /bin/sh -c "\
    cd /lndreviews ;\
    rake posts:new -- -p $PR_NUM -h $REVIEW_HOST -d $REVIEW_DATE "

export PR_NUM=5700 REVIEW_HOST=guggero REVIEW_DATE=2022-05-12
docker run -it --rm --name lndreviews \
  -v $(pwd):/lndreviews \
  --env PR_NUM --env REVIEW_HOST --env REVIEW_DATE \
  lndreviews:dev sh -c "\
  cd /lndreviews ;
  rake posts:new -- -p $PR_NUM -h $REVIEW_HOST -d $REVIEW_DATE \
  "

```

## Changing Site Data

All site configurations are either contained in `_config.yml` or `_data/settings.yml`. Some data is duplicated between the two due to the way Jekyll injects variables, so be sure to update both.

## Running the Test Suite

To run all tests: `rake test` or just `rake`

To run one test file: `rake TEST=test/test_rake_posts_new`

To run an individual test in a test file:
`rake TEST=test/test_rake_posts_new TESTOPTS=--name=test_rake_posts_new`

Before running tests for the first time, you may need to run `bundle update`.

Before running the `test_all_links` test (or all of the tests, which includes
it), the site needs to be started up locally with `make preview`, or with `make
clean preview` if any meeting logs were changed, to pre-render the logs through
the `auto_logs_markup` plugin.

## Attributions

Thanks to [LeNPaul](https://github.com/LeNPaul/jekyll-starter-kit) for the Jekyll starter kit this was forked from and to Will O'Beirne for pointing me in that direction.
