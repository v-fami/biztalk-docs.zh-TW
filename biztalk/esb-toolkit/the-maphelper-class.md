---
title: MapHelper 類別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c552c066-835f-4515-939f-dd465a7a5ed0
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de74610c40b37560abcbce040d80320525f0a21c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295110"
---
# <a name="the-maphelper-class"></a><span data-ttu-id="bab8a-102">MapHelper 類別</span><span class="sxs-lookup"><span data-stu-id="bab8a-102">The MapHelper Class</span></span>
<span data-ttu-id="bab8a-103">使用**MapHelper**類別以執行轉換，直接不使用 Web 服務的轉換。</span><span class="sxs-lookup"><span data-stu-id="bab8a-103">Use the **MapHelper** class to perform transformations directly without using the transformation Web service.</span></span>  
  
 <span data-ttu-id="bab8a-104">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]安裝程式會安裝並註冊組件**Microsof.Practices.ESB.Transform.dll**與**MapHelper**在全域組件快取中的類別。</span><span class="sxs-lookup"><span data-stu-id="bab8a-104">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] installer installs and registers the assembly **Microsof.Practices.ESB.Transform.dll** with the **MapHelper** class in the global assembly cache.</span></span>  
  
 <span data-ttu-id="bab8a-105">**MapHelper**類別會公開兩個公用方法：</span><span class="sxs-lookup"><span data-stu-id="bab8a-105">The **MapHelper** class exposes two public methods:</span></span>  
  
-   <span data-ttu-id="bab8a-106">**TransformMessage**。</span><span class="sxs-lookup"><span data-stu-id="bab8a-106">**TransformMessage**.</span></span> <span data-ttu-id="bab8a-107">包含要轉換之訊息的字串，包含部署在 BizTalk 對應的完整的名稱的字串，這個方法會接受做為參數。</span><span class="sxs-lookup"><span data-stu-id="bab8a-107">This method takes as parameters a string that contains the message to transform and a string that contains the fully qualified name of a map deployed in BizTalk.</span></span> <span data-ttu-id="bab8a-108">方法會傳回字串，包含已轉換的文件。</span><span class="sxs-lookup"><span data-stu-id="bab8a-108">The method returns a string containing the transformed document.</span></span>  
  
-   <span data-ttu-id="bab8a-109">**TransformMessageStream**。</span><span class="sxs-lookup"><span data-stu-id="bab8a-109">**TransformMessageStream**.</span></span> <span data-ttu-id="bab8a-110">包含要轉換的訊息資料流和字串，包含完整部署在 BizTalk 對應的名稱，這個方法會接受做為參數。</span><span class="sxs-lookup"><span data-stu-id="bab8a-110">This method takes as parameters a stream that contains the message to transform and a string that contains the fully qualified name of a map deployed in BizTalk.</span></span> <span data-ttu-id="bab8a-111">方法會傳回字串，包含已轉換的文件。</span><span class="sxs-lookup"><span data-stu-id="bab8a-111">The method returns a string that contains the transformed document.</span></span>