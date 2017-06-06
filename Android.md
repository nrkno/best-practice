# Best practices for Android development at NRK

# Linting

## Policy

* All projects should create a lint error base line (see below)
* All new lint errors should be fixed
* We should work towards fixing all lint errors

## Permissible exceptions

Use common sense. If the lint error is a false positive, just ignore it.


## Create a baseline

Running lint on an existing project can be overwhelming. Take a snapshot of your project's current set of warnings, and then use the snapshot as a baseline for future inspection runs so that only new issues are reported. The baseline snapshot lets you start using lint to fail the build without having to go back and address all existing issues first.

If the project has more than one module, add `abortOnError false` to `lintOptions` in `build.gradle` in each of the modules. This prevents the build failing fatality on the first module and not linting the subsequent modules:

```
android {
    lintOptions {
        abortOnError false
    }
}
```

Then from the command line run

`./gradlew lint`

Find the generated reports

`find . -iname lint-*.xml`

Move each of the reports to the root of its module.

e.g. if you have the following report
```
./android-commons/build/reports/lint-results-debug.xml
```

Move it to the project root

```
mv ./android-commons/build/reports/lint-results-debug.xml ./android-commons/lint-baseline.xml
```

For each module, **remove** `abortOnError false` and add `baseline file("lint-baseline.xml")` to `lintOptions` in `build.gradle`:

```
android {
    lintOptions {
        baseline file("lint-baseline.xml")
    }
}
```
