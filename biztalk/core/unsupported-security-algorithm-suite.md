---
title: 不支援的安全性演算法套件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 11696fed-c3a8-4b11-8249-9f99f7abc8f2
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32b00fea76b95a76cbb6b88f18056bba798e1381
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990983"
---
# <a name="unsupported-security-algorithm-suite"></a><span data-ttu-id="8d298-102">不支援的安全性演算法套件</span><span class="sxs-lookup"><span data-stu-id="8d298-102">Unsupported security algorithm suite</span></span>
## <a name="details"></a><span data-ttu-id="8d298-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8d298-103">Details</span></span>  

|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="8d298-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8d298-104">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="8d298-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="8d298-105">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="8d298-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8d298-106">Event ID</span></span>     |                                         <span data-ttu-id="8d298-107">0</span><span class="sxs-lookup"><span data-stu-id="8d298-107">0</span></span>                                          |
|  <span data-ttu-id="8d298-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="8d298-108">Event Source</span></span>   |                                         <span data-ttu-id="8d298-109">0</span><span class="sxs-lookup"><span data-stu-id="8d298-109">0</span></span>                                          |
|    <span data-ttu-id="8d298-110">元件</span><span class="sxs-lookup"><span data-stu-id="8d298-110">Component</span></span>    |                                         <span data-ttu-id="8d298-111">0</span><span class="sxs-lookup"><span data-stu-id="8d298-111">0</span></span>                                          |
|  <span data-ttu-id="8d298-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8d298-112">Symbolic Name</span></span>  |                                         <span data-ttu-id="8d298-113">0</span><span class="sxs-lookup"><span data-stu-id="8d298-113">0</span></span>                                          |
|  <span data-ttu-id="8d298-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8d298-114">Message Text</span></span>   |                     <span data-ttu-id="8d298-115">不支援的安全性演算法套件： {0}</span><span class="sxs-lookup"><span data-stu-id="8d298-115">Unsupported security algorithm suite: {0}</span></span>                      |

## <a name="explanation"></a><span data-ttu-id="8d298-116">說明</span><span class="sxs-lookup"><span data-stu-id="8d298-116">Explanation</span></span>  
 <span data-ttu-id="8d298-117">當接收位置或傳送埠的安全性演算法套件屬性設定為不正確的值，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="8d298-117">This error occurs when the security algorithm suite property of a receive location or send port is set to an incorrect value.</span></span>  

## <a name="user-action"></a><span data-ttu-id="8d298-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8d298-118">User Action</span></span>  
 <span data-ttu-id="8d298-119">請確定交易通訊協定屬性設為有效的值。</span><span class="sxs-lookup"><span data-stu-id="8d298-119">Ensure that transaction protocol property is set to a valid value.</span></span>  

1. <span data-ttu-id="8d298-120">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="8d298-120">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="8d298-121">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="8d298-121">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  

3. <span data-ttu-id="8d298-122">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="8d298-122">Locate your application and then locate your transport.</span></span>  

4. <span data-ttu-id="8d298-123">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="8d298-123">Right-click the transport name.</span></span>  

5. <span data-ttu-id="8d298-124">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="8d298-124">Click **Properties**.</span></span>  

6. <span data-ttu-id="8d298-125">在 連接埠**型別**清單中，選取**Wcf-nettcp**。</span><span class="sxs-lookup"><span data-stu-id="8d298-125">In the port **Type** list, select **WCF-NetTcp**.</span></span>  

7. <span data-ttu-id="8d298-126">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="8d298-126">Click **Configure**.</span></span>  

8. <span data-ttu-id="8d298-127">在  **Wcf-nettcp 傳輸屬性** 對話方塊中，按一下**安全性** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8d298-127">In the **WCF-NetTcp Transport Properties** dialog box, click the **Security** tab.</span></span>  

9. <span data-ttu-id="8d298-128">在 **訊息安全性**區段中，確定值**演算法套件**正確無誤。</span><span class="sxs-lookup"><span data-stu-id="8d298-128">In the **Message security** section, ensure that the values for **Algorithm suite** are correct.</span></span>
