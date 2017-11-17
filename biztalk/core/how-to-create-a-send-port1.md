---
title: "如何建立傳送 Port1 |Microsoft 文件"
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
ms.assetid: bf32e9f5-ebed-43d2-b9a9-6ab91925d973
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf49b16da34c5341059db34d6874b7099ab54df6
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-create-a-send-port"></a><span data-ttu-id="af6e7-102">如何建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="af6e7-102">How to Create a Send Port</span></span>
<span data-ttu-id="af6e7-103">使用下列程序建立 JD Edwards EnterpriseOne 的 BizTalk Server 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="af6e7-103">Use the following procedure to create BizTalk Server send ports for JD Edwards EnterpriseOne.</span></span>  
  
### <a name="to-create-a-send-port"></a><span data-ttu-id="af6e7-104">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="af6e7-104">To create a send port</span></span>  
  
1.  <span data-ttu-id="af6e7-105">以滑鼠右鍵按一下 [傳送埠] 節點。</span><span class="sxs-lookup"><span data-stu-id="af6e7-105">Right-click the Send Ports node.</span></span>  
  
2.  <span data-ttu-id="af6e7-106">按一下**新增傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="af6e7-106">Click **Add Send Port**.</span></span>  
  
3.  <span data-ttu-id="af6e7-107">在**建立新傳送埠**對話方塊中，選取**靜態請求-回應連接埠**從**指定傳送埠類型**清單，然後按**確定**.</span><span class="sxs-lookup"><span data-stu-id="af6e7-107">In the **Create New Send Port** dialog box, select **Static Solicit-Response Port** from the **Specify the type of Send Port** list, and click **OK**.</span></span>  
  
     <span data-ttu-id="af6e7-108">**靜態請求-回應傳送埠屬性**視窗隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="af6e7-108">The **Static Solicit-Response Send Port Properties** window opens.</span></span>  
  
4.  <span data-ttu-id="af6e7-109">輸入傳送埠名稱，例如`SSOSendToJDEEntOne`。</span><span class="sxs-lookup"><span data-stu-id="af6e7-109">Type a name for the send port, for example, `SSOSendToJDEEntOne`.</span></span>  
  
5.  <span data-ttu-id="af6e7-110">按一下**傳輸**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="af6e7-110">Click **Transport** in the left pane.</span></span>  
  
6.  <span data-ttu-id="af6e7-111">按一下**傳輸類型**，然後選取**[jdeentone]**。</span><span class="sxs-lookup"><span data-stu-id="af6e7-111">Click **Transport Type**, and select **JDEEntOne**.</span></span>  
  
7.  <span data-ttu-id="af6e7-112">選取**位址 (URI)**，然後按一下省略符號 （...） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="af6e7-112">Select the **Address (URI)**, and click the ellipsis (…) button.</span></span>  
  
     <span data-ttu-id="af6e7-113">JD Edwards EnterpriseOne**傳輸屬性** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="af6e7-113">The JD Edwards EnterpriseOne **Transport Properties** dialog box appears.</span></span>  
  
8.  <span data-ttu-id="af6e7-114">型別`myJDEEntOneSSO`如**邏輯系統名稱**。</span><span class="sxs-lookup"><span data-stu-id="af6e7-114">Type `myJDEEntOneSSO` for the **Logical System Name**.</span></span>  
  
9. <span data-ttu-id="af6e7-115">選取**是**如**使用 SSO**。</span><span class="sxs-lookup"><span data-stu-id="af6e7-115">Select **Yes** for **Use SSO**.</span></span>  
  
10. <span data-ttu-id="af6e7-116">在下拉式清單中，選取您建立來代表 JD Edwards EnterpriseOne 系統的單一登入 (SSO) 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="af6e7-116">In the drop-down list, select the Single Sign-On (SSO) affiliate application that you created to represent the JD Edwards EnterpriseOne system.</span></span>  
  
     <span data-ttu-id="af6e7-117">按一下**確定**以確認您輸入的資訊。</span><span class="sxs-lookup"><span data-stu-id="af6e7-117">Click **OK** to confirm the information you entered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af6e7-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af6e7-118">See Also</span></span>  
 <span data-ttu-id="af6e7-119">[建立分支機構應用程式](../core/creating-affiliate-applications4.md) </span><span class="sxs-lookup"><span data-stu-id="af6e7-119">[Creating Affiliate Applications](../core/creating-affiliate-applications4.md) </span></span>  
 [<span data-ttu-id="af6e7-120">BizTalk Adapter for JD Edwards EnterpriseOne 中的安全性</span><span class="sxs-lookup"><span data-stu-id="af6e7-120">Security in BizTalk Adapter for JD Edwards EnterpriseOne</span></span>](../core/security-in-biztalk-adapter-for-jd-edwards-enterpriseone.md)