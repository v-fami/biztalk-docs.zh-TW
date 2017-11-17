---
title: "警告-自訂延伸模組 XML 但找不到自訂 XSLT |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.warning.customExtensionXmlButNoCustomXSLT
ms.assetid: 3219c73c-2e58-4fe2-bc6e-2d60348d2415
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b626f8ede3231c04ae74dc0097cbdf524c90522
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="warning---custom-extension-xml-but-no-custom-xslt"></a><span data-ttu-id="8ce32-102">警告-自訂延伸模組 XML 但找不到自訂 XSLT</span><span class="sxs-lookup"><span data-stu-id="8ce32-102">Warning - Custom Extension XML But No Custom XSLT</span></span>
<span data-ttu-id="8ce32-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="8ce32-103">**Error Code**</span></span>  
  
 <span data-ttu-id="8ce32-104">btm1033</span><span class="sxs-lookup"><span data-stu-id="8ce32-104">btm1033</span></span>  
  
 <span data-ttu-id="8ce32-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="8ce32-105">**Explanation**</span></span>  
  
 <span data-ttu-id="8ce32-106">**自訂延伸模組 XML**屬性但未覆寫**自訂 XSLT 路徑**遭到覆寫的屬性。</span><span class="sxs-lookup"><span data-stu-id="8ce32-106">The **Custom Extension XML** property has been overridden without the **Custom XSLT Path** property being overridden.</span></span> <span data-ttu-id="8ce32-107">若您是刻意這樣做，則可以略過此警告。</span><span class="sxs-lookup"><span data-stu-id="8ce32-107">If this is intentional, you can ignore this warning.</span></span>  
  
 <span data-ttu-id="8ce32-108">BizTalk 對應工具將使用產生的 XSLT (透過編譯對應)，也將產生延伸模組 XML 並將它附加到自訂延伸模組 XML (由覆寫屬性所指定)。</span><span class="sxs-lookup"><span data-stu-id="8ce32-108">BizTalk Mapper will use the XSLT produced by compiling the map and will also generate the Extension XML and append it to the custom Extension XML specified by the overridden property.</span></span> <span data-ttu-id="8ce32-109">這有助於進行對應包含**指令碼處理**運算質使用內嵌 XSLT 或內嵌 XSLT 呼叫範本，讓外部組件中的一個或多個方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="8ce32-109">This can be useful when the map contains **Scripting** functoids that use inline XSLT or inline XSLT call templates that make calls to one or more methods in external assemblies.</span></span> <span data-ttu-id="8ce32-110">在這種情況下，使用者可以接著指定組件名稱對應中的前置詞**自訂延伸模組 XML**屬性。</span><span class="sxs-lookup"><span data-stu-id="8ce32-110">In such cases, the user can then specify the prefix to assembly name mapping in the **Custom Extension XML** property.</span></span>  
  
 <span data-ttu-id="8ce32-111">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="8ce32-111">**User Action**</span></span>  
  
 <span data-ttu-id="8ce32-112">如果此警告所指定的條件不是有意的請提供相容值給**自訂 XSLT 路徑**屬性或移除覆寫值**自訂延伸模組 XML**屬性。</span><span class="sxs-lookup"><span data-stu-id="8ce32-112">If the condition indicated by this warning was not intentional, either provide a compatible value for the **Custom XSLT Path** property or remove the override value for the **Custom Extension XML** property.</span></span>