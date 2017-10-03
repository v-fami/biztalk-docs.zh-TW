---
title: "如何設定傳送管線的 JD Edwards EnterpriseOne |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards EnterpriseOne adapters, send pipelines
- send pipelines, configuring [JD Edwards EnterpriseOne adapters]
- adapters [JD Edwards EnterpriseOne adapters], configuring
- adapters [JD Edwards EnterpriseOne adapters], send pipelines
- JD Edwards EnterpriseOne adapters, configuring
ms.assetid: 4cfcecc1-febe-47c8-b75f-2b84defcdbbc
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c9a6337195c8050afca1f12a015ec492db7f7ae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-send-pipelines-for-jd-edwards-enterpriseone"></a><span data-ttu-id="bf54c-102">如何設定 JD Edwards EnterpriseOne 的傳送管線</span><span class="sxs-lookup"><span data-stu-id="bf54c-102">How to Set Send Pipelines for JD Edwards EnterpriseOne</span></span>
<span data-ttu-id="bf54c-103">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 需要您選取**XMLTransmit**和**XMLReceive**傳送和接收管線分別。</span><span class="sxs-lookup"><span data-stu-id="bf54c-103">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne requires that you select **XMLTransmit** and **XMLReceive** for the send and receive pipelines respectively.</span></span>  
  
### <a name="to-set-pipelines"></a><span data-ttu-id="bf54c-104">設定管線</span><span class="sxs-lookup"><span data-stu-id="bf54c-104">To set pipelines</span></span>  
  
1.  <span data-ttu-id="bf54c-105">在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 所需應用程式。</span><span class="sxs-lookup"><span data-stu-id="bf54c-105">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="bf54c-106">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="bf54c-106">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="bf54c-107">在**傳送埠屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="bf54c-107">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="bf54c-108">輸入傳送埠名稱，例如`SendToJDEEnterpriseOne`。</span><span class="sxs-lookup"><span data-stu-id="bf54c-108">Type a name for the send port, for example, `SendToJDEEnterpriseOne`.</span></span>  
  
    2.  <span data-ttu-id="bf54c-109">從**類型**下拉式清單中，選取**JDE EnterpriseOne**。</span><span class="sxs-lookup"><span data-stu-id="bf54c-109">From the **Type** drop-down list, select **JDE EnterpriseOne**.</span></span>  
  
    3.  <span data-ttu-id="bf54c-110">從**傳送處理常式**下拉式清單中，選取 URI。</span><span class="sxs-lookup"><span data-stu-id="bf54c-110">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="bf54c-111">從 傳送管線 下拉式清單中，選取  **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="bf54c-111">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="bf54c-112">從**接收管線**下拉式清單中，選取**[microsoft.biztalk.defaultpiplelines.xmlreceive]**。</span><span class="sxs-lookup"><span data-stu-id="bf54c-112">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
4.  <span data-ttu-id="bf54c-113">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="bf54c-113">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf54c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf54c-114">See Also</span></span>  
 [<span data-ttu-id="bf54c-115">建立 JD Edwards EnterpriseOne 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="bf54c-115">Creating JD Edwards EnterpriseOne Send Handlers</span></span>](../core/creating-jd-edwards-enterpriseone-send-handlers.md)