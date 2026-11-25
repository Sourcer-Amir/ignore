Write-Host "=== 1. TODOS LOS DISCOS ===" -ForegroundColor Cyan
Get-Disk | Select-Object Number, FriendlyName, BusType, OperationalStatus, Size

Write-Host "`n=== 2. DISPOSITIVOS USB CON ERROR O DESCONOCIDOS ===" -ForegroundColor Cyan
Get-PnpDevice | Where-Object { $_.Status -ne 'OK' -or $_.Class -eq 'USB' -or $_.Class -eq 'Ports' } | Select-Object Status, Class, FriendlyName, InstanceId