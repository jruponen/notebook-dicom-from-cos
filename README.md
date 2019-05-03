# Example of reading DICOM images from Cloud Object Storage
Jukka Ruponen / IBM, 2019-05-03

The method used  will first **download the file from COS** and then access the file locally in the Notebook.

**Reason:**
It seems that S3 (COS) StreamingBody access to DICOM file (which generates a buffered IO-object) does not retain the metadata in the resulting object. To get full .dcm file, with all it's metadata retained, it seems the way is to download it first and then access it from the underlying file system (GPFS).

**Note:**
If you'd need to iterate with and download multiple files in S3 (COS) bucket, there are plenty of examples in the web how to do this.
Search for instance "boto3 download multiple files" and then change the script below according to your needs.

**INSTRUCTIONS:**

Prepare COS with DICOM data:
1. Create a new (or use existing) Cloud Object Storage from [IBM Cloud Catalog](https://cloud.ibm.com/catalog/services/cloud-object-storage)
2. On the COS service dashboard, create new 'Bucket' to store your DICOM files
3. Create (or download) some DICOM files and place them on your Cloud Object Storage, in the 'Bucket' you created

Add new Notebook:
1. Create a new project in [Watson Studio](https://dataplatform.cloud.ibm.com)
2. On the **Assets** tab, press **Add New Notebook**
3. Select **From URL** and set the following values:  
  Name: DICOM sample  
  Notebook URL: https://github.com/jruponen/notebook-dicom-from-cos/raw/master/DICOM%20test%20v2.ipynb  
  Select runtime: Leave it to "Default Python 3.5 XS (2 vCPU and 8 GB RAM)"  
4. Press **Create Notebook**
5. Open the Notebook and follow step-by-step instructions
