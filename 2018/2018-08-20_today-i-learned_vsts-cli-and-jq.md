# 2018-08-20 Today I learned - VSTS CLI and jq

tags: az, azure devops, bash, cli, command line, json, jq, vsts

Today I learned about the [VSTS command line](https://docs.microsoft.com/en-us/cli/vsts/overview?view=vsts-cli-latest) tool from a colleague.

I might actually have heard about it before, but wasn't able to try it out because I was previously using the on-premise TFS and not the cloud based VSTS, but hey, today I tried it out :)

For example, you can query VSTS for pull requests you've created by doing the following:


```shell
$ cd /your-vsts-git-repo
$ vsts login
$ vsts code pr list --creator "James Barrow"
```

This will return a JSON object containing info about what pull requests you have created.

If you don't really care about the entire structure, you can then use another command line tool I've come across before called [jq](https://stedolan.github.io/jq/).

For example, if you only care about the title, status and url of the pull request, you could do the following:


```shell
$ vsts code pr list --creator "James Barrow" | jq ".[] | { title, status, url }"
```

That's a long command, but what it basically does is pipes the JSON result into jq, which parses it by taking each element in the array of the result, and then filtering it to only take the title, status and url properties of each item in the array.

And finally, since we all know the best way to use git is via the command line and git bash, you can then also create a bash alias in your `~/.bashrc` file:


```
alias prs='vsts code pr list --creator "James Barrow" | jq ".[] | {title,status,url}"'
```

So you can just check for your pull requests now by simply running:


```shell
$ prs
{
  "title": "RE #1234 - some pull request",
  "status": "active",
  "url": "https://blah.visualstudio.com/.../pullRequests/2345"
}
```

Which gives you something like that ;)

Much simpler than having to open up Chrome, go to VSTS, find the right tab for pull requests, etc...

I want to dig more into using jq to pull out info on if the pull requests have had votes as well, so I can just run a command from my command line and see if I need to follow up on a PR or not, but this will have to wait for another day :)

One last note is that use of single and double quotes might be important depending on your shell of choice, so keep that in mind too.

Hope this helped someone.

<b>Update 1:</b> There is also `vsts code pr list -o table` which prints a nicer table format

<b>Update 2:</b> This is now part of the [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)


