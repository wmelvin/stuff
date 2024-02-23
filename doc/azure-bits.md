# Azure Bits

Using the Azure CLI in PowerShell, write the list of images published by Microsoft, and available in eastus, to a CSV file on the Desktop.

```powershell
az vm image list --all --location eastus --publisher Microsoft | ConvertFrom-Json | Export-Csv -Path ([IO.Path]::Combine([Environment]::GetFolderPath("Desktop"), "azure-image-list.csv"))
```

Change **location** to other than `eastus` as needed.

---
