# satel-pr-commenter
This GitHub action posts comments on a PR when a workflow fails

# Usage

```yml
pr-commenter-action
  runs-on: ubuntu-latest
  if: always()
  needs: [<PREVIOUS-JOBS>]
  steps:
  - name: pr-action 
    uses: SatelCreative/satel-pr-commenter@1.0.0
    if: ${{ github.ref != 'refs/heads/main' && !contains(github.ref, 'refs/tags/') }}
    with:
      token: ${{ secrets.GITHUB_TOKEN }}
      job_status: ${{ needs.set-variables.result }}  
      body: "<FAQ-COMMENT>"
      number: ${{ github.event.pull_request.number }}
      author: ${{ github.event.pull_request.user.login }}
```
