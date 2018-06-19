---
title: 程式設計 Guide1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- developing, programming guide
- programming guide
ms.assetid: fb2d5e3b-1907-49c4-806d-a2604c702322
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 230ecf4cf9b735bdc2d4e68fc233799e95bb3182
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26004679"
---
# <a name="programming-guide"></a><span data-ttu-id="37aa2-102">程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="37aa2-102">Programming Guide</span></span>
<span data-ttu-id="37aa2-103">[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]程式設計指南說明適用於開發人員撰寫的程式碼與 BTAHL7 的概念和程序。</span><span class="sxs-lookup"><span data-stu-id="37aa2-103">The [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Programming Guide explains concepts and procedures for developers writing code with BTAHL7.</span></span> <span data-ttu-id="37aa2-104">使用本指南搭配[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]文件。</span><span class="sxs-lookup"><span data-stu-id="37aa2-104">Use this guide in conjunction with [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37aa2-105">閱讀本指南之前, 您應該熟悉[!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)]程式開發，BizTalk Server 和[HL7 加速器，可用的 BizTalk 工具深入了解](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md)。</span><span class="sxs-lookup"><span data-stu-id="37aa2-105">Before reading this guide, you should be familiar with [!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)] development, BizTalk Server, and [Learn the HL7 accelerator and the BizTalk tools available](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="37aa2-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="37aa2-106">In This Section</span></span>  
  
-   [<span data-ttu-id="37aa2-107">處理 HL7 訊息</span><span class="sxs-lookup"><span data-stu-id="37aa2-107">Processing HL7 Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)  
  
-   [<span data-ttu-id="37aa2-108">使用 HL7 2.X 結構描述</span><span class="sxs-lookup"><span data-stu-id="37aa2-108">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)  
  
-   [<span data-ttu-id="37aa2-109">使用 HL7 2.XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="37aa2-109">Using HL7 2.XML Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)  
  
-   [<span data-ttu-id="37aa2-110">處理 MLLP 編碼訊息</span><span class="sxs-lookup"><span data-stu-id="37aa2-110">Processing MLLP-encoded Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)  
  
-   [<span data-ttu-id="37aa2-111">建立及處理通知</span><span class="sxs-lookup"><span data-stu-id="37aa2-111">Creating and Processing Acknowledgments</span></span>](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)  
  
-   [<span data-ttu-id="37aa2-112">使用動態資料驗證</span><span class="sxs-lookup"><span data-stu-id="37aa2-112">Using Dynamic Data Validation</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-dynamic-data-validation.md)  
  
-   [<span data-ttu-id="37aa2-113">建立用於稽核和記錄事件的 WMI 接收</span><span class="sxs-lookup"><span data-stu-id="37aa2-113">Creating a WMI Sink for Auditing and Logging Events</span></span>](../../adapters-and-accelerators/accelerator-hl7/creating-a-wmi-sink-for-auditing-and-logging-events.md)  
  
-   [<span data-ttu-id="37aa2-114">其他資源</span><span class="sxs-lookup"><span data-stu-id="37aa2-114">Additional Resources</span></span>](../../adapters-and-accelerators/accelerator-hl7/additional-resources.md)