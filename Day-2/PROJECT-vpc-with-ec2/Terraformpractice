terraform {
  required_providers {
    google = {
      source = "registry.terraform.io/hashicorp/google"
      version = ">=1.0"
    }
  }
}

provider "google" {
  project = "terraformpractice-458504"
  region  = "us-central1"
  credentials = "key.json"
}

resource "google_storage_bucket" "terraformbucket" {
  name          = "lokeshasi7768"
  location      = "us-central1"
  force_destroy = true

  lifecycle_rule {
    condition {
      age = 3
    }
    action {
      type = "Delete"
    }
  }
}

resource "google_compute_instance" "default" {
  name  = "lokeshasi7768"
  machine_type = "e2-micro"
  zone = "us-central1-c"

  // boot disk
  boot_disk {
    auto_delete = true
    device_name = "lokeshasi7768"
	
	initialize_params {
      image = "projects/debian-cloud/global/images/debian-12-bookworm-v20250415"
      size  = 10
      type  = "pd-balanced"
	  }
  }

  // networking
  network_interface {
    network = "default"
        subnetwork = "default"
        stack_type = "IPV4_ONLY"
  }

  lifecycle {
    create_before_destroy = true
  }
 }
