---
description: 了解详细信息： CorDebugRegister 枚举
title: CorDebugRegister 枚举
ms.date: 03/30/2017
api_name:
- CorDebugRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugRegister
helpviewer_keywords:
- CorDebugRegister enumeration [.NET Framework debugging]
ms.assetid: 003bb138-7960-4291-ac88-0d87e470ff70
topic_type:
- apiref
ms.openlocfilehash: 7a5dc771a239a82448f898e2f518e920993ec35a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661865"
---
# <a name="cordebugregister-enumeration"></a><span data-ttu-id="552f0-103">CorDebugRegister 枚举</span><span class="sxs-lookup"><span data-stu-id="552f0-103">CorDebugRegister Enumeration</span></span>

<span data-ttu-id="552f0-104">指定与给定处理器体系结构关联的寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-104">Specifies the registers associated with a given processor architecture.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="552f0-105">语法</span><span class="sxs-lookup"><span data-stu-id="552f0-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRegister {  
  
    REGISTER_INSTRUCTION_POINTER = 0,  
    REGISTER_STACK_POINTER,  
    REGISTER_FRAME_POINTER,  
  
    REGISTER_X86_EIP = 0,  
    REGISTER_X86_ESP,  
    REGISTER_X86_EBP,  
  
    REGISTER_X86_EAX,  
    REGISTER_X86_ECX,  
    REGISTER_X86_EDX,  
    REGISTER_X86_EBX,  
  
    REGISTER_X86_ESI,  
    REGISTER_X86_EDI,  
  
    REGISTER_X86_FPSTACK_0,  
    REGISTER_X86_FPSTACK_1,  
    REGISTER_X86_FPSTACK_2,  
    REGISTER_X86_FPSTACK_3,  
    REGISTER_X86_FPSTACK_4,  
    REGISTER_X86_FPSTACK_5,  
    REGISTER_X86_FPSTACK_6,  
    REGISTER_X86_FPSTACK_7,  
  
    REGISTER_AMD64_RIP = 0,  
    REGISTER_AMD64_RSP,  
    REGISTER_AMD64_RBP,  
    REGISTER_AMD64_RAX,  
    REGISTER_AMD64_RCX,  
    REGISTER_AMD64_RDX,  
    REGISTER_AMD64_RBX,  
    REGISTER_AMD64_RSI,  
    REGISTER_AMD64_RDI,  
    REGISTER_AMD64_R8,  
    REGISTER_AMD64_R9,  
    REGISTER_AMD64_R10,  
    REGISTER_AMD64_R11,  
    REGISTER_AMD64_R12,  
    REGISTER_AMD64_R13,  
    REGISTER_AMD64_R14,  
    REGISTER_AMD64_R15,  
  
    REGISTER_AMD64_XMM0,  
    REGISTER_AMD64_XMM1,  
    REGISTER_AMD64_XMM2,  
    REGISTER_AMD64_XMM3,  
    REGISTER_AMD64_XMM4,  
    REGISTER_AMD64_XMM5,  
    REGISTER_AMD64_XMM6,  
    REGISTER_AMD64_XMM7,  
    REGISTER_AMD64_XMM8,  
    REGISTER_AMD64_XMM9,  
    REGISTER_AMD64_XMM10,  
    REGISTER_AMD64_XMM11,  
    REGISTER_AMD64_XMM12,  
    REGISTER_AMD64_XMM13,  
    REGISTER_AMD64_XMM14,  
    REGISTER_AMD64_XMM15,  
  
    REGISTER_IA64_BSP = REGISTER_FRAME_POINTER,  
    REGISTER_IA64_R0  = REGISTER_IA64_BSP + 1,  
    REGISTER_IA64_F0  = REGISTER_IA64_R0  + 128,  
    REGISTER_ARM_PC = 0,  
    REGISTER_ARM_SP,  
    REGISTER_ARM_R0,  
    REGISTER_ARM_R1,  
    REGISTER_ARM_R2,  
    REGISTER_ARM_R3,  
    REGISTER_ARM_R4,  
    REGISTER_ARM_R5,  
    REGISTER_ARM_R6,  
    REGISTER_ARM_R7,  
    REGISTER_ARM_R8,  
    REGISTER_ARM_R9,  
    REGISTER_ARM_R10,  
    REGISTER_ARM_R11,  
    REGISTER_ARM_R12,  
    REGISTER_ARM_LR,  
  
} CorDebugRegister;  
```  
  
## <a name="members"></a><span data-ttu-id="552f0-106">成员</span><span class="sxs-lookup"><span data-stu-id="552f0-106">Members</span></span>  
  
|<span data-ttu-id="552f0-107">成员</span><span class="sxs-lookup"><span data-stu-id="552f0-107">Member</span></span>|<span data-ttu-id="552f0-108">说明</span><span class="sxs-lookup"><span data-stu-id="552f0-108">Description</span></span>|  
|------------|-----------------|  
|`REGISTER_INSTRUCTION_POINTER`|<span data-ttu-id="552f0-109">任何处理器上的指令指针寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-109">An instruction pointer register on any processor.</span></span>|  
|`REGISTER_STACK_POINTER`|<span data-ttu-id="552f0-110">任何处理器上的堆栈指针寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-110">A stack pointer register on any processor.</span></span>|  
|`REGISTER_FRAME_POINTER`|<span data-ttu-id="552f0-111">任何处理器上的帧指针寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-111">A frame pointer register on any processor.</span></span>|  
|`REGISTER_X86_EIP`|<span data-ttu-id="552f0-112">x86 处理器上的指令指针寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-112">The instruction pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESP`|<span data-ttu-id="552f0-113">x86 处理器上的堆栈指针寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-113">The stack pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBP`|<span data-ttu-id="552f0-114">x86 处理器上的基指针寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-114">The base pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EAX`|<span data-ttu-id="552f0-115">x86 处理器上的 A 数据寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-115">The A data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ECX`|<span data-ttu-id="552f0-116">x86 处理器上的 C 数据寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-116">The C data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDX`|<span data-ttu-id="552f0-117">x86 处理器上的 D 数据寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-117">The D data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBX`|<span data-ttu-id="552f0-118">x86 处理器上的 B 数据寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-118">The B data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESI`|<span data-ttu-id="552f0-119">x86 处理器上的源索引寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-119">The source index register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDI`|<span data-ttu-id="552f0-120">x86 处理器上的目标索引寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-120">The destination index register on the x86 processor.</span></span>|  
|`REGISTER_X86_FPSTACK_0`|<span data-ttu-id="552f0-121">x86 浮点 (FP) 处理器上的堆栈寄存器 0。</span><span class="sxs-lookup"><span data-stu-id="552f0-121">The stack register 0 on the x86 floating-point (FP) processor.</span></span>|  
|`REGISTER_X86_FPSTACK_1`|<span data-ttu-id="552f0-122">x86 FP 处理器上的 #1 堆栈寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-122">The #1 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_2`|<span data-ttu-id="552f0-123">x86 FP 处理器上的 #2 堆栈寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-123">The #2 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_3`|<span data-ttu-id="552f0-124">x86 FP 处理器上的 #3 堆栈寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-124">The #3 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_4`|<span data-ttu-id="552f0-125">x86 FP 处理器上的 #4 堆栈寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-125">The #4 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_5`|<span data-ttu-id="552f0-126">x86 FP 处理器上的 #5 堆栈寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-126">The #5 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_6`|<span data-ttu-id="552f0-127">x86 FP 处理器上的 #6 堆栈寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-127">The #6 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_7`|<span data-ttu-id="552f0-128">x86 FP 处理器上的 #7 堆栈寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-128">The #7 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_AMD64_RIP`|<span data-ttu-id="552f0-129">AMD64 处理器上的指令指针寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-129">The instruction pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSP`|<span data-ttu-id="552f0-130">AMD64 处理器上的堆栈指针寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-130">The stack pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBP`|<span data-ttu-id="552f0-131">AMD64 处理器上的基指针寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-131">The base pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RAX`|<span data-ttu-id="552f0-132">AMD64 处理器上的 A 数据寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-132">The A data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RCX`|<span data-ttu-id="552f0-133">AMD64 处理器上的 C 数据寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-133">The C data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDX`|<span data-ttu-id="552f0-134">AMD64 处理器上的 D 数据寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-134">The D data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBX`|<span data-ttu-id="552f0-135">AMD64 处理器上的 B 数据寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-135">The B data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSI`|<span data-ttu-id="552f0-136">AMD64 处理器上的源索引寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-136">The source index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDI`|<span data-ttu-id="552f0-137">AMD64 处理器上的目标索引寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-137">The destination index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R8`|<span data-ttu-id="552f0-138">AMD64 处理器上的 #8 数据寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-138">The #8 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R9`|<span data-ttu-id="552f0-139">AMD64 处理器上的 #9 数据寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-139">The #9 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R10`|<span data-ttu-id="552f0-140">AMD64 处理器上的 #10 数据寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-140">The #10 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R11`|<span data-ttu-id="552f0-141">AMD64 处理器上的 #11 数据寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-141">The #11 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R12`|<span data-ttu-id="552f0-142">AMD64 处理器上的 #12 数据寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-142">The #12 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R13`|<span data-ttu-id="552f0-143">AMD64 处理器上的 #13 数据寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-143">The #13 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R14`|<span data-ttu-id="552f0-144">AMD64 处理器上的 #14 数据寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-144">The #14 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R15`|<span data-ttu-id="552f0-145">AMD64 处理器上的 #15 数据寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-145">The #15 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM0`|<span data-ttu-id="552f0-146">AMD64 处理器上的 #0 多媒体寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-146">The #0 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM1`|<span data-ttu-id="552f0-147">AMD64 处理器上的 #1 多媒体寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-147">The #1 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM2`|<span data-ttu-id="552f0-148">AMD64 处理器上的 #2 多媒体寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-148">The #2 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM3`|<span data-ttu-id="552f0-149">AMD64 处理器上的 #3 多媒体寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-149">The #3 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM4`|<span data-ttu-id="552f0-150">AMD64 处理器上的 #4 多媒体寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-150">The #4 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM5`|<span data-ttu-id="552f0-151">AMD64 处理器上的 #5 多媒体寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-151">The #5 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM6`|<span data-ttu-id="552f0-152">AMD64 处理器上的 #6 多媒体寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-152">The #6 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM7`|<span data-ttu-id="552f0-153">AMD64 处理器上的 #7 多媒体寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-153">The #7 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM8`|<span data-ttu-id="552f0-154">AMD64 处理器上的 #8 多媒体寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-154">The #8 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM9`|<span data-ttu-id="552f0-155">AMD64 处理器上的 #9 多媒体寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-155">The #9 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM10`|<span data-ttu-id="552f0-156">AMD64 处理器上的 #10 多媒体寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-156">The #10 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM11`|<span data-ttu-id="552f0-157">AMD64 处理器上的 #11 多媒体寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-157">The #11 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM12`|<span data-ttu-id="552f0-158">AMD64 处理器上的 #12 多媒体寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-158">The #12 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM13`|<span data-ttu-id="552f0-159">AMD64 处理器上的 #13 多媒体寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-159">The #13 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM14`|<span data-ttu-id="552f0-160">AMD64 处理器上的 #14 多媒体寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-160">The #14 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM15`|<span data-ttu-id="552f0-161">AMD64 处理器上的 #15 多媒体寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-161">The #15 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_IA64_BSP`|<span data-ttu-id="552f0-162">IA-64 处理器上的堆栈指针寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-162">The stack pointer register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_R0`|<span data-ttu-id="552f0-163">IA-64 处理器上的 #0 数据寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-163">The #0 data register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_F0`|<span data-ttu-id="552f0-164">IA-64 处理器上的 #0 FP 数据寄存器。</span><span class="sxs-lookup"><span data-stu-id="552f0-164">The #0 FP data register on the IA-64 processor.</span></span>|  
|`REGISTER_ARM_PC`|<span data-ttu-id="552f0-165">ARM 处理器上的程序计数器寄存器 (R15)。</span><span class="sxs-lookup"><span data-stu-id="552f0-165">The program counter register (R15) on the ARM processor.</span></span>|  
|`REGISTER_ARM_SP`|<span data-ttu-id="552f0-166">ARM 处理器上的堆栈指针寄存器 (R13)。</span><span class="sxs-lookup"><span data-stu-id="552f0-166">The stack pointer register (R13) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R0`|<span data-ttu-id="552f0-167">ARM 处理器上的数据寄存器 R0。</span><span class="sxs-lookup"><span data-stu-id="552f0-167">Data register R0 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R1`|<span data-ttu-id="552f0-168">ARM 处理器上的数据寄存器 R1。</span><span class="sxs-lookup"><span data-stu-id="552f0-168">Data register R1 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R2`|<span data-ttu-id="552f0-169">ARM 处理器上的数据寄存器 R2。</span><span class="sxs-lookup"><span data-stu-id="552f0-169">Data register R2 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R3`|<span data-ttu-id="552f0-170">ARM 处理器上的数据寄存器 R3。</span><span class="sxs-lookup"><span data-stu-id="552f0-170">Data register R3 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R4`|<span data-ttu-id="552f0-171">ARM 处理器上的寄存器 R4。</span><span class="sxs-lookup"><span data-stu-id="552f0-171">Register R4 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R5`|<span data-ttu-id="552f0-172">ARM 处理器上的寄存器 R5。</span><span class="sxs-lookup"><span data-stu-id="552f0-172">Register R5 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R6`|<span data-ttu-id="552f0-173">ARM 处理器上的寄存器 R6。</span><span class="sxs-lookup"><span data-stu-id="552f0-173">Register R6 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R7`|<span data-ttu-id="552f0-174">ARM 处理器上的寄存器 R7（THUMB 帧指针）。</span><span class="sxs-lookup"><span data-stu-id="552f0-174">Register R7 (the THUMB frame pointer) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R8`|<span data-ttu-id="552f0-175">ARM 处理器上的寄存器 R8。</span><span class="sxs-lookup"><span data-stu-id="552f0-175">Register R8 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R9`|<span data-ttu-id="552f0-176">ARM 处理器上的寄存器 R9。</span><span class="sxs-lookup"><span data-stu-id="552f0-176">Register R9 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R10`|<span data-ttu-id="552f0-177">ARM 处理器上的寄存器 R10。</span><span class="sxs-lookup"><span data-stu-id="552f0-177">Register R10 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R11`|<span data-ttu-id="552f0-178">ARM 处理器上的帧指针。</span><span class="sxs-lookup"><span data-stu-id="552f0-178">The frame pointer on the ARM processor.</span></span>|  
|`REGISTER_ARM_R12`|<span data-ttu-id="552f0-179">ARM 处理器上的寄存器 R12。</span><span class="sxs-lookup"><span data-stu-id="552f0-179">Register R12 on the ARM processor.</span></span>|  
|`REGISTER_ARM_LR`|<span data-ttu-id="552f0-180">ARM 处理器上的链接寄存器 (R14)。</span><span class="sxs-lookup"><span data-stu-id="552f0-180">The link register (R14) on the ARM processor.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="552f0-181">备注</span><span class="sxs-lookup"><span data-stu-id="552f0-181">Remarks</span></span>  

 <span data-ttu-id="552f0-182">IA-64 处理器上共有 128 种通用数据寄存器和 128 种浮点数据寄存器，但只提供了值 `REGISTER_IA64_R0` 和 `REGISTER_IA64_F0`。</span><span class="sxs-lookup"><span data-stu-id="552f0-182">There are 128 general-purpose data registers and 128 floating-point data registers on the IA-64 processor, but only values `REGISTER_IA64_R0` and `REGISTER_IA64_F0` are provided.</span></span> <span data-ttu-id="552f0-183">可按如下方式确定其他值：</span><span class="sxs-lookup"><span data-stu-id="552f0-183">The other values can be determined as follows:</span></span>  
  
- <span data-ttu-id="552f0-184">将寄存器号与 `REGISTER_IA64_R0` 相加，获得值 `REGISTER_IA64_R1` 到 `REGISTER_IA64_R127`（对应于 IA-64 处理器上的 #1 数据寄存器到 #127 数据寄存器）。</span><span class="sxs-lookup"><span data-stu-id="552f0-184">Add the register number to `REGISTER_IA64_R0` for values `REGISTER_IA64_R1` through `REGISTER_IA64_R127`, which correspond to the #1 data register through the #127 data register on the IA-64 processor.</span></span>  
  
- <span data-ttu-id="552f0-185">将寄存器号与 `REGISTER_IA64_F0` 相加，获得值 `REGISTER_IA64_F1` 到 `REGISTER_IA64_F127`（对应于 IA-64 处理器上的 #1 FP 数据寄存器到 #127 FP 数据寄存器）。</span><span class="sxs-lookup"><span data-stu-id="552f0-185">Add the register number to `REGISTER_IA64_F0` for values `REGISTER_IA64_F1` through `REGISTER_IA64_F127`, which correspond to the #1 FP data register through the #127 FP data register on the IA-64 processor.</span></span>  
  
 <span data-ttu-id="552f0-186">例如，如果需要指定 IA-64 处理器上的 #83 数据寄存器，请使用 `REGISTER_IA64_R0` + 83。</span><span class="sxs-lookup"><span data-stu-id="552f0-186">For example, if you need to specify the #83 data register on the IA-64 processor, use `REGISTER_IA64_R0` + 83.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="552f0-187">要求</span><span class="sxs-lookup"><span data-stu-id="552f0-187">Requirements</span></span>  

 <span data-ttu-id="552f0-188">**平台：** 请参阅 [系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="552f0-188">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="552f0-189">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="552f0-189">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="552f0-190">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="552f0-190">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="552f0-191">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="552f0-191">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="552f0-192">请参阅</span><span class="sxs-lookup"><span data-stu-id="552f0-192">See also</span></span>

- [<span data-ttu-id="552f0-193">调试枚举</span><span class="sxs-lookup"><span data-stu-id="552f0-193">Debugging Enumerations</span></span>](debugging-enumerations.md)
