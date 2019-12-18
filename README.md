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

## CSRSS
```
NTSTATUS
WINAPI
BasepNotifyCsrOfThread(IN HANDLE ThreadHandle,
                       IN PCLIENT_ID ClientId)
{
    BASE_API_MESSAGE ApiMessage;
    PBASE_CREATE_THREAD CreateThreadRequest = &ApiMessage.Data.CreateThreadRequest;

    DPRINT("BasepNotifyCsrOfThread: Thread: %p, Handle %p\n",
            ClientId->UniqueThread, ThreadHandle);

    /* Fill out the request */
    CreateThreadRequest->ClientId = *ClientId;
    CreateThreadRequest->ThreadHandle = ThreadHandle;

    /* Call CSR */
    CsrClientCallServer((PCSR_API_MESSAGE)&ApiMessage,
                        NULL,
                        CSR_CREATE_API_NUMBER(BASESRV_SERVERDLL_INDEX, BasepCreateThread),
                        sizeof(*CreateThreadRequest));
    if (!NT_SUCCESS(ApiMessage.Status))
    {
        DPRINT1("Failed to tell CSRSS about new thread: %lx\n", ApiMessage.Status);
        return ApiMessage.Status;
    }

    /* Return Success */
    return STATUS_SUCCESS;
}
```
