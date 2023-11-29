# program-committee-h-index
Get the h-index and related metrics for a long list of people, e.g. the program committee for a conference

This notebook uses Publish or Perish command line tools to calculate metrics.
The bulk of the notebook is simply wrapping those tools, calling them in a reasonable way, and collating the results.

> [!IMPORTANT]  
> - It is best to get Google Scholar profile page URLS from the PC. In that case, only `retrieve_gs` and `metrics_gs` are needed, and there is no ambiguity (i.e. multiple profile pages with the same name)
> - If `search_gs` is used, input names should match Google Scholar, e.g. if Google Scholar says "Christopher Conway", then "Chris Conway" is less likely to match

## Process

1. I queried Google Scholar using the name and affiliation as given in the input file

2. If this returned no hits, I tried again without affiliation

3. If more than one Google Scholar profile matched, I used the keywords associated with that profile (if available) and did a semantic match with "artificial intelligence education data mining learning". I then used the profile with the highest match

4. Publication info for the "best" profile was downloaded and then metrics calculated. h-index is column "h" and citations is column "c"

Possible errors:

- A profile was never found. This seems to happen if the name in the file is the familiar name version of the formal name used in Google Scholar. Missing profiles are at the bottom of the attached sheet are require manual entry.

- A profile was found, but it is the wrong profile. In this case, there are usually multiple profiles and the wrong one was chosen. To double check this, you can use the following columns:

  - "matches" shows how many profiles matched. If more than 1, might be worth checking

  - "scholar name" shows the name of the "best" profile. **If the first/last name is different, it should definitely be checked.**

  - "scholar url" is the url of the "best" profile. If you open the csv in excel, this should be a clickable hyperlink you can use to easily check this profile is the correct profile.
