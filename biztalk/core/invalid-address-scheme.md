---
title: 無效的位址配置 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b059289-654e-40d6-a092-2a685e6e10f7
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 385f3aca555f18599887897f6b60144070f252a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257790"
---
# <a name="invalid-address-scheme"></a><span data-ttu-id="0cdc5-102">無效的位址配置</span><span class="sxs-lookup"><span data-stu-id="0cdc5-102">Invalid address scheme</span></span>
## <a name="details"></a><span data-ttu-id="0cdc5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0cdc5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0cdc5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0cdc5-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="0cdc5-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="0cdc5-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="0cdc5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0cdc5-106">Event ID</span></span>|<span data-ttu-id="0cdc5-107">000</span><span class="sxs-lookup"><span data-stu-id="0cdc5-107">000</span></span>|  
|<span data-ttu-id="0cdc5-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="0cdc5-108">Event Source</span></span>|<span data-ttu-id="0cdc5-109">0</span><span class="sxs-lookup"><span data-stu-id="0cdc5-109">0</span></span>|  
|<span data-ttu-id="0cdc5-110">元件</span><span class="sxs-lookup"><span data-stu-id="0cdc5-110">Component</span></span>|<span data-ttu-id="0cdc5-111">0</span><span class="sxs-lookup"><span data-stu-id="0cdc5-111">0</span></span>|  
|<span data-ttu-id="0cdc5-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0cdc5-112">Symbolic Name</span></span>|<span data-ttu-id="0cdc5-113">0</span><span class="sxs-lookup"><span data-stu-id="0cdc5-113">0</span></span>|  
|<span data-ttu-id="0cdc5-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0cdc5-114">Message Text</span></span>|<span data-ttu-id="0cdc5-115">無效的位址配置。必須是"{0}"配置。</span><span class="sxs-lookup"><span data-stu-id="0cdc5-115">Invalid address scheme; expecting "{0}" scheme.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0cdc5-116">說明</span><span class="sxs-lookup"><span data-stu-id="0cdc5-116">Explanation</span></span>  
 <span data-ttu-id="0cdc5-117">您提供一種通訊協定配置，不符合您的傳輸繫結所定義的型別。</span><span class="sxs-lookup"><span data-stu-id="0cdc5-117">You provided a protocol scheme that does not match the type defined by your transport binding.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0cdc5-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0cdc5-118">User Action</span></span>  
 <span data-ttu-id="0cdc5-119">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="0cdc5-119">To resolve this error, do the following:</span></span>  
  
1.  <span data-ttu-id="0cdc5-120">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** ，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="0cdc5-120">Click **Start**, click **All Programs**, click **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**, and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="0cdc5-121">在 主控台根目錄中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="0cdc5-121">In the Console Root, expand  **BizTalk Server Administration**, expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="0cdc5-122">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="0cdc5-122">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="0cdc5-123">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="0cdc5-123">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="0cdc5-124">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="0cdc5-124">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="0cdc5-125">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="0cdc5-125">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="0cdc5-126">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="0cdc5-126">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="0cdc5-127">在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**一般**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0cdc5-127">In the **WCF [***transport type***] Transport Properties** dialog box, click the **General** tab.</span></span>  
  
9. <span data-ttu-id="0cdc5-128">在**位址 (URI)** 文字方塊中，確認位址值，與 WCF 配接器所使用的類型相符。</span><span class="sxs-lookup"><span data-stu-id="0cdc5-128">In the **Address (URI)** text box, ensure that address value matches the type of the WCF adapter that is being used.</span></span>  
  
 <span data-ttu-id="0cdc5-129">此外，如果您使用 Wcf-custom 配接器搭配系統提供繫結型別時，檢查的值**繫結型別**清單**繫結** 索引標籤。如果**繫結型別**設定為**customBinding**，地址應符合傳輸繫結項目中所列**繫結型別**清單**繫結** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0cdc5-129">Also, if you use the WCF-Custom adapter with a system-provided binding type, check the value of the **Binding Type** list on the **Binding** tab. If the **Binding Type** is configured to **customBinding**, the address should match the transport binding element listed in the **Binding Type** list on the **Binding** tab.</span></span>