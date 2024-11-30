# Repair Windows

Run the following commands as admin to fix corrupted files:

    DISM /Online /Cleanup-Image /RestoreHealth
    sfc /scannow