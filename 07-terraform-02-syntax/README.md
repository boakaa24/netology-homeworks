1.
Для YandexCloud для создания образов можно использовать packer.
2.  
```
terraform {
  required_providers {
    yandex = {
      source = "yandex-cloud/yandex"
    }
  }
  required_version = ">= 0.13"
}

provider "yandex" {
  token     = "token.json"
  cloud_id  = "b1g86urqpc774okk45j5"
  folder_id = "b1gk2jk55lrll6pbdk70"
  zone      = "ru-central1-a"
}

resource "yandex_compute_image" "vm1" {
  name          =  "ubuntu-20-04-lts-v20220620"
  source_image  = "fd8f1tik9a7ap9ik2dg1"
}
```
```
root@ubuntu-home:~/Terraform# terraform plan

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # yandex_compute_image.vm1 will be created
  + resource "yandex_compute_image" "vm1" {
      + created_at      = (known after apply)
      + folder_id       = (known after apply)
      + id              = (known after apply)
      + min_disk_size   = (known after apply)
      + name            = "ubuntu-20-04-lts-v20220620"
      + os_type         = (known after apply)
      + pooled          = (known after apply)
      + product_ids     = (known after apply)
      + size            = (known after apply)
      + source_disk     = (known after apply)
      + source_family   = (known after apply)
      + source_image    = "fd8f1tik9a7ap9ik2dg1"
      + source_snapshot = (known after apply)
      + source_url      = (known after apply)
      + status          = (known after apply)
    }

Plan: 1 to add, 0 to change, 0 to destroy.

──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────

Note: You didn't use the -out option to save this plan, so Terraform can't guarantee to take exactly these actions if you run "terraform
apply" now.
```
