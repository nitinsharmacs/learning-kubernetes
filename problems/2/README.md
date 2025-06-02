# Make Service Account token accessible inside pod as projected volume.

## Requirements

1. Token should have permissions to access pods inside namespace where pod is running.
2. Access means, list, get, create and delete.
