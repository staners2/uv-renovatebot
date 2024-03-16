# Demonstrate expected behavior 
Issue: https://github.com/renovatebot/renovate/issues/27841#issuecomment-1988321345

## Steps
1. Write dependencies in `pyproject.toml` in the block `dependencies`
2. Create `renovate.json`
3. Generate lock file - `requirements.txt`
```
uv pip compile --no-cache --extra tests pyproject.toml -o requirements.txt
```
4. Starts RenovateBot and wait until it creates `PullRequest`
5. Watch created `PullRequest`


# Actual result
Renovate create `PullRequest` where it update version only in `pyproject.toml`, 
but not updated dependencies version in `requirements.txt`

# Expected result
Renovate create `PullRequest` where it update version in `pyproject.toml` and 
exec command `uv pip compile --no-cache --extra tests pyproject.toml -o requirements.txt` 
to updated dependencies version in `requirements.txt`