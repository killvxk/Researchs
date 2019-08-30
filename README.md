# Researchs
一些研究

## ETW
EtwThreatIntProvRegHandle - called from KeInsertQueueApc and IopfCompleteRequest  
EtwTiLogSetContextThread - called from PspWow64SetContextThread & PspSetContextThreadInternal  
EtwTiLogAllocExecVm - called from MiAllocateVirtualMemory  
EtwTiLogProtectExecVm - called from NtProtectVirtualMemory  
EtwTiLogReadWriteVm - called from MiReadWriteVirtualMemory  
EtwTiLogDeviceObjectLoadUnload - called from IoDeleteDevice & IoCreateDevice  
EtwTiLogDriverObjectLoad - called from IopLoadDriver & IoCreateDriver  
EtwTiLogMapExecView - called from NtMapViewOfSection & MiMapViewOfSectionExCommon  
EtwTiLogSuspendResumeProcess - called from PsThawProcess, PsFreezeProcess, PsResumeProcess & PsSuspendProcess  
EtwTiLogSuspendResumeThread - called from PsSuspendThread & PsResumeThread  

## RPC
### msrpc.sys
msrpc.sys 真香
