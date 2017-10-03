---
title: "如何建立 JD Edwards OneWorld 傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating send ports
- send ports, creating
ms.assetid: 858425ef-bdb7-4d2d-90ca-b3655e389749
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc77fd72171983ab2fbc7de42ddf36d770d045c6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-send-ports-for-jd-edwards-oneworld"></a><span data-ttu-id="b617d-102">如何建立 JD Edwards OneWorld 的傳送埠</span><span class="sxs-lookup"><span data-stu-id="b617d-102">How to Create Send Ports for JD Edwards OneWorld</span></span>
<span data-ttu-id="b617d-103">使用下列程序來建立傳送埠。</span><span class="sxs-lookup"><span data-stu-id="b617d-103">Use the following procedure to create a send port.</span></span>  
  
### <a name="to-create-a-send-port"></a><span data-ttu-id="b617d-104">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="b617d-104">To create a send port</span></span>  
  
1.  <span data-ttu-id="b617d-105">在 BizTalk Server 管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後瀏覽至必要的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b617d-105">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then navigate to the required application.</span></span>  
  
2.  <span data-ttu-id="b617d-106">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="b617d-106">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b617d-107">您也可以使用**靜態單向連接埠**。</span><span class="sxs-lookup"><span data-stu-id="b617d-107">You can also use **Static One-Way Port**.</span></span>  
  
3.  <span data-ttu-id="b617d-108">在**傳送埠屬性**對話方塊中，於**名稱**欄位中，輸入傳送埠名稱 (例如，輸入**SendToJDE**。)</span><span class="sxs-lookup"><span data-stu-id="b617d-108">In the **Send Port Properties** dialog box, in the **Name** field, type a send port name (for example, type **SendToJDE**.)</span></span>  
  
4.  <span data-ttu-id="b617d-109">在**類型**下拉式清單中，選取**[jdeoneworld]**。</span><span class="sxs-lookup"><span data-stu-id="b617d-109">In the **Type** drop-down list, select **JDEOneWorld**.</span></span>  
  
5.  <span data-ttu-id="b617d-110">在**URI**下拉式清單中，選取傳送處理常式。</span><span class="sxs-lookup"><span data-stu-id="b617d-110">In the **URI** drop-down list, select the send handler.</span></span>  
  
6.  <span data-ttu-id="b617d-111">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b617d-111">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b617d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b617d-112">See Also</span></span>  
 [<span data-ttu-id="b617d-113">建立 JD Edwards OneWorld 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="b617d-113">Creating JD Edwards OneWorld Send Handlers</span></span>](../core/creating-jd-edwards-oneworld-send-handlers.md)