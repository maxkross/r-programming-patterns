# Friendly Functions

## Including Examples

It's often useful to [include](http://r-pkgs.had.co.nz/inst.html) example files
that are distributed with your package so that users can try out your functions
even if they don't have their own files or data. For easy access to these files
it's a good idea to include a function like `mypackage_example()` which returns
the path to an example file. You can find sample code for this function below:


```r
#' Get path to mypackage example
#'
#' mypackage comes bundled with some example files in its `inst/extdata`
#' directory. This function make them easy to access.
#'
#' @param path Name of file. If `NULL`, the example files will be listed.
#' @export
#' @examples
#' mypackage_example()
#' mypackage_example("data.csv")
mypackage_example <- function(path = NULL) {
  if (is.null(path)) {
    dir(system.file("extdata", package = "mypackage"))
  } else {
    system.file("extdata", path, package = "mypackage", mustWork = TRUE)
  }
}
```

### Real World Examples

- [readxl](https://github.com/tidyverse/readxl/blob/master/R/example.R)
