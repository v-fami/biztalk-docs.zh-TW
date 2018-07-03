---
title: 如何偵錯對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1ee1e26-fced-4126-b48a-71007043424d
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f30d26b7c722ea4e4896bc7d19130e41eec5c719
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989719"
---
# <a name="how-to-debug-maps"></a><span data-ttu-id="e5dae-102">如何偵錯對應</span><span class="sxs-lookup"><span data-stu-id="e5dae-102">How to Debug Maps</span></span>
<span data-ttu-id="e5dae-103">**偵錯對應**項功能可用於找出並修正複雜的對應問題。</span><span class="sxs-lookup"><span data-stu-id="e5dae-103">The **Debug Map** feature is useful in identifying and fixing complex mapping issues.</span></span> <span data-ttu-id="e5dae-104">本主題提供使用內嵌 XSLT 偵錯工具進行對應偵錯的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="e5dae-104">This topic provides step-by-step instructions for debugging maps using the inline XSLT debugger.</span></span>  

> [!NOTE]
>  <span data-ttu-id="e5dae-105">偵錯對應時**偵錯對應**功能會使用對應檔屬性**TestMap 輸入執行個體**並**TestMap 輸出執行個體**。</span><span class="sxs-lookup"><span data-stu-id="e5dae-105">When debugging the map, the **Debug Map** feature uses the map file properties **TestMap Input Instance** and **TestMap Output Instance**.</span></span> <span data-ttu-id="e5dae-106">因此，建議您在偵錯對應之前先設定對應檔中的輸入與輸出執行個體屬性。</span><span class="sxs-lookup"><span data-stu-id="e5dae-106">Therefore, before you debug the map, we recommend that you configure the input and output instance properties in the map file.</span></span>  

### <a name="to-debug-a-biztalk-map"></a><span data-ttu-id="e5dae-107">若要偵錯 BizTalk 對應</span><span class="sxs-lookup"><span data-stu-id="e5dae-107">To debug a BizTalk map</span></span>  

1. <span data-ttu-id="e5dae-108">在 方案總管 中，以滑鼠右鍵按一下您想要測試，然後按一下 的地圖**偵錯對應**。</span><span class="sxs-lookup"><span data-stu-id="e5dae-108">In Solution Explorer, right-click the map you want to test, and then click **Debug Map**.</span></span> [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]<span data-ttu-id="e5dae-109"> 會在其編輯器中以 XSLT 格式顯示對應。</span><span class="sxs-lookup"><span data-stu-id="e5dae-109"> displays the map in XSLT format in its editor.</span></span>  

2. <span data-ttu-id="e5dae-110">按 F10 或 F11 偵錯 XSL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="e5dae-110">Press F10 or F11 to debug the XSL code.</span></span> <span data-ttu-id="e5dae-111">如果您在運算質呼叫上按 F11，[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 會進入該運算質的 C# 程式碼。</span><span class="sxs-lookup"><span data-stu-id="e5dae-111">When you press F11 on a functoid call, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] steps into the C# code for the functoid.</span></span> <span data-ttu-id="e5dae-112">您可以檢視運算質中的原始程式碼本機 Windows 偵錯工具中使用的變數值。</span><span class="sxs-lookup"><span data-stu-id="e5dae-112">You can view the values of variables used in the functoid source code in the Local Windows Debugger.</span></span>
