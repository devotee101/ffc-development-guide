# Source code
The default position for FFC is that code should be open source and hosted within GitHub.  

If there is a need for a private repository, for example when source controlling infrastructure as code, that should be controlled within FFC's hosted GitLab.  

## Branching strategies
FFC aims to be a true DevOps programme with capability to deliver value often and rapidly.

To support this, there are two branching strategy options, `Feature branch development` and `Trunk based development`.  Feature branch development should be preferred as it has significantly lower risk and promotes more collaboration.  However, there may be some scenarios where a trunk based development approach can deliver more value.

### Feature branch development
With feature branch development, all feature development should take place in a dedicated branch instead of the master branch. 

This allows multiple developers to work on a feature whilst protecting the master branch. 

New branches should be created from master for both feature development and bug fixes.

![Feature branch development](/docs/images/feature-branch-development.png)

#### Pros
- more control over Master​
- increased opportunity for collaboration through pull requests​
- broken builds can automatically be kept out of Master​
- supports remote working and a experience variation​
- features can be tested in isolated PR environment before approval​

#### Cons
- feature branches can be long lived
- prone to larger merge conflicts

#### Notes
- well refined user stories can reduce feature branch scope
- good collaboration on how to implement a feature can reduce code review time

### Trunk based development
With trunk based development, developers commit code directly to the master branch.

This allows for a more rapid CI/CD approach, but needs to be well supported with robust working practices.  

![Trunk based development](/docs/images/trunk-based-development.png)

#### Pros
- no long running feature branches
- changes can be implemented quickly
- less admin from branch creation and pull requests

#### Cons
- depends on developers running builds locally
- no way to automatically prevent broken builds into master branch
- difficult to support when there is experience variation or remote working

#### Notes
- feature flags and branching by abstraction can support long running changes
- pair programming can reduce risk through real time code review

## Pull Requests
When following feature branch development, pull requests should be used to collaborate and ensure code quality.

Pull requests should be created in line with [Defra's standards](https://github.com/DEFRA/software-development-standards/blob/master/processes/pull_requests.md) and reviewed in the spirit of [FFC's code review standards](/docs/code-review.md).

Pull requests should trigger a build and a PR deployment to support the view.

### Completing Pull Request
In order to complete a pull request, all of the following conditions must be met:
- at least one approver
- PR build must complete successfully

On completion of a pull request a squash merge should be performed and the feature/bug branch should be deleted.  The commit message should be amended to give a concise description of the changes, rather than the default list of individual commits.
