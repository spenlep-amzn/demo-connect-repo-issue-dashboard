# Compare Start/End Dates

At end of shift, take a snapshop of the current main branch:

1. Head to https://github.com/spencerlepine/poc-github-dashboard/releases
2. Create release
3. Click "Choose a tag" => Enter "myname/end-of-oncall-5/01"
4. Publish the release
5. Now fine the commitId (e.g. 3983ac2) on main branch - dated at start of shift
6. Head to command line, in root directory of code base
7. Run `git tag myname/start-of-oncall-5/01 3983ac2 && git push origin --tags`
8. Compare the two tags now! https://github.com/spencerlepine/poc-github-dashboard/compare/spencer/start-of-oncall-5/14...spencer/end-of-oncall-5/18?short_path=e6e4e96#diff-e6e4e962c8b605d863101398cd3d70058c3c9f5f6604656d3998df43ad85f84e
9. Open 'files changed', click "display rich diff" to load images if needed
10. Save the link in a release: https://github.com/spencerlepine/poc-github-dashboard/releases

> Note: if you create a tag for on the day the shift starts, it will be easy. Otherwise, you can't create tags in the UI for commits that are older than 3 days :(