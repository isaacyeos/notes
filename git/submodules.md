# Submodules
Let's say we have 3 remote repos (and no submodule references have been created yet):
- test (parent repo)
- test_submodule (we will add this as a submodule of test repo)
- test_submodule_submodule (we will add this as a submodule of test_submodule repo)

## Scenarios

1. Assuming we have the test repo cloned on our local machine. To add a remote repo as a submodule of current project (eg: adding test_submodule as a submodule of test) (we assume here that test_submodule is the folder where test_submodule was cloned into, which is the default):

    ```shell
    cd test
    git submodule add <test_submodule remote repo url>
    git add .gitmodules test_submodule
    git commit -m "added submodule"
    git push
    ```

2. A new commit from a code change is made to the remote test_submodule repo. We want our test repo's test_submodule to point to this latest commit:

    ```shell
    git submodule update --remote --merge
    git add test_submodule
    git commit -m "updated submodule"
    git push
    ```

3. Now let's say we want to add a submodule to test_submodule. Repeat step 1 to add test_submodule_submodule as a submodule of test_submodule. This creates a new commit to the remote test_submodule repo.

4. Now we want our test repo's test_submodule to point to the latest commit of the remote test_submodule repo. However, doing step 2 will only update code changes to the test_submodule repo (including the commit ID of test_submodule_submodule that it is pointing to), but will not get code from test_submodule_submodule. Instead, an empty folder called test_submodule_submodule will be created. Since this is the first time we are cloning test_submodule_submodule, we need to do the following:

    ```shell
    git submodule update --remote --merge
    git add test_submodule
    git commit -m "updated submodule"
    git push
    git submodule update --recursive --init
    ```

    Note that we need to commit the updated test_submodule commit id first before we do a git submodule update --recursive.

5. Subsequently, if new commits are made to test_submodule_submodule and test_submodule, since we have already cloned test_submodule_submodule, we can update our test repo with the following (without --init):

    ```shell
    git submodule update --remote --merge
    git add test_submodule
    git commit -m "updated submodule"
    git push
    git submodule update --recursive
    ```

6. To clone a repo with all its submodules:
    ```shell
    git clone --recursive <repo_url>
    ```
    This will clone all the submodules with the commit IDs specified in the parent repos.

7. To pull the latest changes from a remote repo with submodules, if you need to clonse any uninitialized submodules:

    ```shell
    git pull
    git submodule update --recursive --init
    ```

    If all submodules have already been cloned:
    ```shell
    git pull
    git submodule update --recursive
    ```

    This will update all submodules to the commit IDs specified in their parent repos.