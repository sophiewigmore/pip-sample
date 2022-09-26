# Python sample app using pip package manager

## Building

This app has uses a vulnerable version of `gunicorn` (Pip-installed dependency), and `pip`.

`pack build pip-sample --buildpack paketo-buildpacks/python --sbom-output-dir sbom-content`

## Looking for vulnerabilities

#### Snyk on image
```
docker scan pip-sample
```
Locates OS-based vulnerabilities, but no Pip-related vulnerabilities.

#### Grype on image
```
grype pip-sample
```
Locates OS-level vulnerabilities AND high-severity `gunicorn` vulnerability

#### Grype on SBOM
```
grype sbom:sbom-content/build/paketo-buildpacks_pip/pip/sbom.syft.json
grype sbom:sbom-content/launch/paketo-buildpacks_pip-install/packages/sbom.syft.json
```
Locates high-severity `gunicorn` vulnerability AND high-severity `pip` vulnerability
