---
title: imm_atomic_exch (sm5 - asm)
description: Immediate atomic exchange to memory.
ms.assetid: D06AE57E-52A4-4579-84FF-7DE9E713A5E3
ms.topic: reference
ms.date: 05/31/2018
---

# imm\_atomic\_exch (sm5 - asm)

Immediate atomic exchange to memory.



| imm\_atomic\_exch dst0\[.single\_component\_mask\], dst1, dstAddress\[.swizzle\], src0\[.select\_component\] |
|--------------------------------------------------------------------------------------------------------------|



 



| Item                                                                                                           | Description                                                                                                                       |
|----------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| <span id="dst0"></span><span id="DST0"></span>*dst0*<br/>                                                | \[in\] Contains the value from *dst1* before the write.<br/>                                                                |
| <span id="dst1"></span><span id="DST1"></span>*dst1*<br/>                                                | \[in\] An unordered access view (UAV) (u\#). In the Compute Shader this can also be Thread Group Shared Memory (g\#). <br/> |
| <span id="dstAddress"></span><span id="dstaddress"></span><span id="DSTADDRESS"></span>*dstAddress*<br/> | \[in\] The memory address.<br/>                                                                                             |
| <span id="src0"></span><span id="SRC0"></span>*src0*<br/>                                                | \[in\] The value to write to *dst1* at *dstAddress*.<br/>                                                                   |



 

## Remarks

This instruction performs a single component 32-bit value write of operand *src0* to *dst1* at 32-bit per component address *dstAddress*.

If *dst1* is a u\#, it may have been declared as raw, typed or structured. If typed, it must be declared as UINT/SINT with the bound resource format being R32\_UINT/\_SINT.

If *dst1* is g\#, it must be declared as raw or structured.

The number of components taken from the address is determined by the dimensionality of the resource declared at *dst1*.

The original 32-bit value in the destination memory is written to *dst0*.

The entire operation is performed atomically.

If the shader invocation is inactive, for example if the pixel has been discarded earlier in its execution, or a pixel/sample invocation only exists to serve as a helper to a real pixel/sample for derivatives, this instruction does not alter the *dst1* memory at all, and the returned value is undefined.

Out of bounds addressing on u\# causes nothing to be written to memory, except if the u\# is structured, and byte offset into the struct (second component of the address) is causing the out of bounds access, then the entire contents of the UAV become undefined.

Out of bounds addressing on u\# or g\# causes an undefined result to be returned to the shader in *dst0*.

This instruction applies to the following shader stages:



| Vertex | Hull | Domain | Geometry | Pixel | Compute |
|--------|------|--------|----------|-------|---------|
|        |      |        |          | X     | X       |



 

Because UAVs are available at all shader stages for Direct3D 11.1, this instruction applies to all shader stages for the Direct3D 11.1 runtime, which is available starting with Windows 8.



| Vertex | Hull | Domain | Geometry | Pixel | Compute |
|--------|------|--------|----------|-------|---------|
| X      | X    | X      | X        | X     | X       |



 

## Minimum Shader Model

This instruction is supported in the following shader models:



| Shader Model                                              | Supported |
|-----------------------------------------------------------|-----------|
| [Shader Model 5](d3d11-graphics-reference-sm5.md)        | yes       |
| [Shader Model 4.1](dx-graphics-hlsl-sm4.md)              | no        |
| [Shader Model 4](dx-graphics-hlsl-sm4.md)                | no        |
| [Shader Model 3 (DirectX HLSL)](dx-graphics-hlsl-sm3.md) | no        |
| [Shader Model 2 (DirectX HLSL)](dx-graphics-hlsl-sm2.md) | no        |
| [Shader Model 1 (DirectX HLSL)](dx-graphics-hlsl-sm1.md) | no        |



 

## Related topics

<dl> <dt>

[Shader Model 5 Assembly (DirectX HLSL)](shader-model-5-assembly--directx-hlsl-.md)
</dt> </dl>

 

 





