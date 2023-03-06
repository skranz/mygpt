# mygpt


# 1. Overview

There are already packages that create ChatGPT Addins for RStudio:

https://github.com/MichelNivard/gptstudio

https://github.com/jcrodriguez1989/chatgpt

While partly replicating existing functionality, this package mainly contributes as folowing:

1. Users are motivated to experiment, create and customize their own Addins using simple YAML based templates.

2. By default all usage of ChatGPT will be logged in a local folder. This is mainly helpful for students who are asked to document how they used ChatGPT in a thesis or project.

## Installation via r-universe:

```r
install.packages('gpt4r', repos = c('https://skranz.r-universe.dev', 'https://cloud.r-project.org'))
```

# 2. First steps without customization

You can first use and test mygpt without any customization.

1. Install the package (see above)

2. Get and specify an OpenAI API key as explained below.

3. Then open some document in RStudio, select some text and click on some mygpt addin in RStudio's `Addins` dropdown.


## Using without OpenAI API key: Just copy prompts to clipboard

If you don't want yet to use an OpenAI API key (see below), you can use the package to copy prompts to the clipboard that you can then manually paste in ChatGPT's (or Bing Chat's) web interface. If no API key is found, prompt generation the default. If you want to just generate prompts even an API key is there, call:
```r
set_gpt_default_action("copy_prompt")
```

To revert to the default, i.e. running OpenAI's API, call:

```r
set_gpt_default_action("run")
```

## Set OpenAI API Key

To properly use the package, you should set up your OpenAI API key in R.

1. You need to [sign-up to OpenAI](https://platform.openai.com/signup). You probably can first test the API for a limited time and volume free of charge.

2. Then you must generate an API Key under your account setting. See also [Best Practices for API Key
Safety](https://help.openai.com/en/articles/5112595-best-practices-for-api-key-safety).

3. Then you have to assign your API key for usage in R, this can be done
just for the actual session, by doing:

``` r
Sys.setenv(OPENAI_API_KEY = "XX-XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX")
```

Or you can create a text file `openai.key` containing just the key as string in the directory of the documents that you modify. If `gpt4rstudio` finds such a text file, it loads the key from it. 

# 3. Customizing ChatGPT Addins via Templates

Here just a short description.

1. Make a local copy of the `mygpt` repository, e.g. by downloading its [ZIP from Github](https://github.com/skranz/mygpt/archive/refs/heads/main.zip)

2. Open the project in RStudio and check whether you can build the R package by `Build -> Install and Restart`.

3. Go to the directory `inst/templates` where you find the YAML templates for the different addons. The templates describe the ChatGPT prompt, some additional API parameters like `temperature` and how the results are shown in RStudio. Currently, there is no good documentation, but I hope most things become clear by looking at the examples. You can create new template files or change existing ones.

4. Call `Addins -> mygpt -> Update mygpt` to update the package, including the addins to the current templates in `inst/templates`.

5. Go on experimenting and using the package!

