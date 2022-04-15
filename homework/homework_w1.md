# Homework Week 1

## Question 1
### Install Google Cloud SDK. What's the version you have?

`Google Cloud SDK 379.0.0`

`bq 2.0.74`

`core 2022.03.25`

`gsutil 5.8`

## Question 2
### Output of running `terraform init`, `terraform plan`, `terraform apply` 

```
AzureAD+MarkvanKruistum@LAPTOP-G2OBT40J MINGW64 /c/development/data-engineering-zoomcamp/week_1_basics_n_setup/1_terraform_gcp/terraform (main)
$ terraform init

Initializing the backend...

Successfully configured the backend "local"! Terraform will automatically
use this backend unless the backend configuration changes.

Initializing provider plugins...
- Finding latest version of hashicorp/google...
- Installing hashicorp/google v4.15.0...
- Installed hashicorp/google v4.15.0 (signed by HashiCorp)

Terraform has created a lock file .terraform.lock.hcl to record the provider
selections it made above. Include this file in your version control repository
so that Terraform can guarantee to make the same selections by default when
you run "terraform init" in the future.

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.

AzureAD+MarkvanKruistum@LAPTOP-G2OBT40J MINGW64 /c/development/data-engineering-zoomcamp/week_1_basics_n_setup/1_terraform_gcp/terraform (main)
$ terraform plan
var.project
  Your GCP Project ID

  Enter a value: de-zoomcamp-346214


Terraform used the selected providers to generate the following execution
plan. Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # google_bigquery_dataset.dataset will be created
  + resource "google_bigquery_dataset" "dataset" {
      + creation_time              = (known after apply)
      + dataset_id                 = "trips_data_all"
      + delete_contents_on_destroy = false
      + etag                       = (known after apply)
      + id                         = (known after apply)
      + last_modified_time         = (known after apply)
      + location                   = "europe-west6"
      + project                    = "de-zoomcamp-346214"
      + self_link                  = (known after apply)

      + access {
          + domain         = (known after apply)
          + group_by_email = (known after apply)
          + role           = (known after apply)
          + special_group  = (known after apply)
          + user_by_email  = (known after apply)

          + dataset {
              + target_types = (known after apply)

              + dataset {
                  + dataset_id = (known after apply)
                  + project_id = (known after apply)
                }
            }

          + view {
              + dataset_id = (known after apply)
              + project_id = (known after apply)
              + table_id   = (known after apply)
            }
        }
    }

  # google_storage_bucket.data-lake-bucket will be created
  + resource "google_storage_bucket" "data-lake-bucket" {
      + force_destroy               = true
      + id                          = (known after apply)
      + location                    = "EUROPE-WEST6"
      + name                        = "dtc_data_lake_de-zoomcamp-346214"
      + project                     = (known after apply)
      + self_link                   = (known after apply)
      + storage_class               = "STANDARD"
      + uniform_bucket_level_access = true
      + url                         = (known after apply)

      + lifecycle_rule {
          + action {
              + type = "Delete"
            }

          + condition {
              + age                   = 30
              + matches_storage_class = []
              + with_state            = (known after apply)
            }
        }

      + versioning {
          + enabled = true
        }
    }

Plan: 2 to add, 0 to change, 0 to destroy.

─────────────────────────────────────────────────────────────────────────────

Note: You didn't use the -out option to save this plan, so Terraform can't
guarantee to take exactly these actions if you run "terraform apply" now.

AzureAD+MarkvanKruistum@LAPTOP-G2OBT40J MINGW64 /c/development/data-engineering-zoomcamp/week_1_basics_n_setup/1_terraform_gcp/terraform (main)
$ terraform apply
var.project
  Your GCP Project ID

  Enter a value: de-zoomcamp-346214


Terraform used the selected providers to generate the following execution
plan. Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # google_bigquery_dataset.dataset will be created
  + resource "google_bigquery_dataset" "dataset" {
      + creation_time              = (known after apply)
      + dataset_id                 = "trips_data_all"
      + delete_contents_on_destroy = false
      + etag                       = (known after apply)
      + id                         = (known after apply)
      + last_modified_time         = (known after apply)
      + location                   = "europe-west6"
      + project                    = "de-zoomcamp-346214"
      + self_link                  = (known after apply)

      + access {
          + domain         = (known after apply)
          + group_by_email = (known after apply)
          + role           = (known after apply)
          + special_group  = (known after apply)
          + user_by_email  = (known after apply)

          + dataset {
              + target_types = (known after apply)

              + dataset {
                  + dataset_id = (known after apply)
                  + project_id = (known after apply)
                }
            }

          + view {
              + dataset_id = (known after apply)
              + project_id = (known after apply)
              + table_id   = (known after apply)
            }
        }
    }

  # google_storage_bucket.data-lake-bucket will be created
  + resource "google_storage_bucket" "data-lake-bucket" {
      + force_destroy               = true
      + id                          = (known after apply)
      + location                    = "EUROPE-WEST6"
      + name                        = "dtc_data_lake_de-zoomcamp-346214"
      + project                     = (known after apply)
      + self_link                   = (known after apply)
      + storage_class               = "STANDARD"
      + uniform_bucket_level_access = true
      + url                         = (known after apply)

      + lifecycle_rule {
          + action {
              + type = "Delete"
            }

          + condition {
              + age                   = 30
              + matches_storage_class = []
              + with_state            = (known after apply)
            }
        }

      + versioning {
          + enabled = true
        }
    }

Plan: 2 to add, 0 to change, 0 to destroy.

Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value: yes

google_bigquery_dataset.dataset: Creating...
google_storage_bucket.data-lake-bucket: Creating...
google_bigquery_dataset.dataset: Creation complete after 1s [id=projects/de-zoomcamp-346214/datasets/trips_data_all]
google_storage_bucket.data-lake-bucket: Creation complete after 2s [id=dtc_data_lake_de-zoomcamp-346214]

Apply complete! Resources: 2 added, 0 changed, 0 destroyed.
```

## Question 3
### How many taxi trips were there on January 15?
```
SELECT COUNT(index) FROM public.yellow_taxi_data
WHERE DATE(tpep_pickup_datetime) = '2021-01-15';
```

53024

## Question 4
### Find the largest tip for each day. On which day it was the largest tip in January?

```
SELECT DATE(tpep_pickup_datetime), MAX(tip_amount) AS total_tip FROM public.yellow_taxi_data
GROUP BY DATE(tpep_pickup_datetime)
ORDER BY total_tip DESC;
```

January 20

## Question 5
### What was the most popular destination for passengers picked up in Central Park on January 14?

```
SELECT t2."Borough", t2."Zone", COUNT(t1."DOLocationID") AS docount FROM public.yellow_taxi_data t1
LEFT JOIN public.zones t2 ON t1."DOLocationID" = t2."LocationID"
WHERE DATE(tpep_pickup_datetime) = '2021-01-14' AND t1."PULocationID" = 43
GROUP BY t1."DOLocationID", t2."Borough", t2."Zone"
ORDER BY docount DESC;
```

Upper East Side South

## Question 6
### What's the pickup-dropoff pair with the largest average price for a ride (calculated based on `total_amount`)?

```
SELECT t3."Zone" AS "PUZone", t2."Zone" AS "DOZone", AVG(t1."total_amount") AS avg_total_amount FROM public.yellow_taxi_data t1
LEFT JOIN public.zones t2 ON t1."DOLocationID" = t2."LocationID"
LEFT JOIN public.zones t3 on t1."PULocationID" = t3."LocationID"
GROUP BY t1."DOLocationID", t3."Zone", t2."Zone"
ORDER BY avg_total_amount DESC;
```

Alphabet City / Unknown