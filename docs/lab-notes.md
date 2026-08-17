# Lab Notes

## Training Context

This repository documents a Google Cloud Skills Boost IAM lab completed in a temporary training environment.

The lab used two temporary user accounts so I could compare permissions, change role assignments, and verify the result from both the Google Cloud console and Cloud Shell.

## Access-Control Sequence

The main access-control sequence was:

1. Review the starting IAM assignments.
2. Verify the second user had Project Viewer access.
3. Confirm the user could read/list existing storage content but could not create a new object.
4. Remove Project Viewer.
5. Confirm the user could no longer list the bucket.
6. Grant Storage Object Viewer.
7. Confirm storage read access was restored without restoring broad project Viewer access.

## Custom Roles

### Privacy Reviewer

Created through the Google Cloud console.

The role used read-oriented permissions across:

- Cloud Storage
- Cloud Bigtable
- Cloud Spanner

### App Viewer

Created through a YAML file and the `gcloud` CLI.

Initial permissions:

```text
appengine.versions.get
appengine.versions.list
compute.instances.get
compute.instances.list
```

Later additions:

```text
container.clusters.get
container.clusters.list
```

## Custom-Role Lifecycle

I worked through:

```text
Created
  ↓
Permissions updated
  ↓
Disabled
  ↓
Deleted
  ↓
Restored with undelete
```

After the role was restored, its stage was still `DISABLED`. Undeleting the role restored the role object but did not automatically enable it.

## Portfolio Notes

This is a training lab rather than an original production implementation.

For the public portfolio copy:

- Temporary student usernames were removed.
- Temporary project IDs were removed.
- Project-scoped resource names were removed where they exposed the temporary project.
- Raw CLI screenshots with repeated temporary identifiers were not included.
- Generic IAM role names, permission names, and `gcloud` concepts are retained because they explain the technical work.
