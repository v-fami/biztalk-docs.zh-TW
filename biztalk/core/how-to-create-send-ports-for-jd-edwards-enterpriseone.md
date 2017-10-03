---
title: "如何建立 JD Edwards EnterpriseOne 的傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards EnterpriseOne adapters, send ports
- send ports, creating [JD Edwards EnterpriseOne adapters]
- adapters [JD Edwards EnterpriseOne adapters], send ports
- send ports, JD Edwards EnterpriseOne adapters
- creating, send ports [JD Edwards EnterpriseOne adapters]
ms.assetid: 687f9207-ad3e-41ea-8640-5b9b6efbc14e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36a3e8d2d3e8e1db230a03d9c4a0351d3a0f8394
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-send-ports-for-jd-edwards-enterpriseone"></a><span data-ttu-id="99979-102">如何建立 JD Edwards EnterpriseOne 的傳送埠</span><span class="sxs-lookup"><span data-stu-id="99979-102">How to Create Send Ports for JD Edwards EnterpriseOne</span></span>
<span data-ttu-id="99979-103">使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 建立傳送埠。</span><span class="sxs-lookup"><span data-stu-id="99979-103">Using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create a send port.</span></span>  
  
### <a name="to-create-a-send-port"></a><span data-ttu-id="99979-104">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="99979-104">To create a send port</span></span>  
  
1.  <span data-ttu-id="99979-105">按一下**啟動**，指向 **所有程式**，指向  **Microsoft BizTalk Server**，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="99979-105">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk Server**, and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="99979-106">在 BizTalk Server 管理主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，並展開**應用程式**，然後展開您要建立傳送埠的應用程式。</span><span class="sxs-lookup"><span data-stu-id="99979-106">In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, and expand **Applications**, and then expand the application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="99979-107">以滑鼠右鍵按一下**傳送埠**按一下**新增**，然後按一下 **靜態請求-回應連接埠**。</span><span class="sxs-lookup"><span data-stu-id="99979-107">Right-click **Send Ports** and click **New**, and then click **Static Solicit-Response Port**.</span></span>  
  
4.  <span data-ttu-id="99979-108">在**傳送埠屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="99979-108">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    -   <span data-ttu-id="99979-109">在**名稱**方塊中，輸入傳送埠名稱 (例如， `SendToJDE`)。</span><span class="sxs-lookup"><span data-stu-id="99979-109">In the **Name** box, type a send port name (for example, `SendToJDE`).</span></span>  
  
    -   <span data-ttu-id="99979-110">從**類型**下拉式清單中，選取**JDEdwards**。</span><span class="sxs-lookup"><span data-stu-id="99979-110">From the **Type** drop-down list, select **JDEdwards**.</span></span>  
  
    -   <span data-ttu-id="99979-111">從**傳送處理常式**下拉式清單中，選取傳送處理常式位址。</span><span class="sxs-lookup"><span data-stu-id="99979-111">From the **Send handler** drop-down list, select the send handler address.</span></span>  
  
5.  <span data-ttu-id="99979-112">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="99979-112">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99979-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99979-113">See Also</span></span>  
 [<span data-ttu-id="99979-114">建立 JD Edwards EnterpriseOne 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="99979-114">Creating JD Edwards EnterpriseOne Send Handlers</span></span>](../core/creating-jd-edwards-enterpriseone-send-handlers.md)