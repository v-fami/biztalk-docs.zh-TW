---
title: "取得 machine.config 從繫結延伸錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65ab48cf-575b-4db6-984a-880f7e286959
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bbe53def02f42c59cf5e40380c898f47695c19da
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="error-getting-binding-extensions-from-machineconfig"></a><span data-ttu-id="6ed83-102">取得 machine.config 從繫結延伸時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="6ed83-102">Error getting binding extensions from machine.config</span></span>
## <a name="details"></a><span data-ttu-id="6ed83-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6ed83-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6ed83-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6ed83-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="6ed83-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="6ed83-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="6ed83-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6ed83-106">Event ID</span></span>|<span data-ttu-id="6ed83-107">0</span><span class="sxs-lookup"><span data-stu-id="6ed83-107">0</span></span>|  
|<span data-ttu-id="6ed83-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="6ed83-108">Event Source</span></span>|<span data-ttu-id="6ed83-109">0</span><span class="sxs-lookup"><span data-stu-id="6ed83-109">0</span></span>|  
|<span data-ttu-id="6ed83-110">元件</span><span class="sxs-lookup"><span data-stu-id="6ed83-110">Component</span></span>|<span data-ttu-id="6ed83-111">0</span><span class="sxs-lookup"><span data-stu-id="6ed83-111">0</span></span>|  
|<span data-ttu-id="6ed83-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6ed83-112">Symbolic Name</span></span>|<span data-ttu-id="6ed83-113">0</span><span class="sxs-lookup"><span data-stu-id="6ed83-113">0</span></span>|  
|<span data-ttu-id="6ed83-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6ed83-114">Message Text</span></span>|<span data-ttu-id="6ed83-115">取得 machine.config 從繫結延伸時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="6ed83-115">Error getting binding extensions from machine.config</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6ed83-116">說明</span><span class="sxs-lookup"><span data-stu-id="6ed83-116">Explanation</span></span>  
 <span data-ttu-id="6ed83-117">當接收位置時，就會發生此錯誤或傳送連接埠繫結組態有使用者定義繫結延伸，但它不會定義在 machine.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="6ed83-117">This error occurs when a  receive location or send port binding configuration has a user defined binding extension, but it is not defined in machine.config file.</span></span> <span data-ttu-id="6ed83-118">主要是搭配 Wcf-custom 和 Wcf-customisolated 配接器，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="6ed83-118">This situation occurs primarily with the WCF-Custom and WCF-CustomIsolated adapters.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6ed83-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6ed83-119">User Action</span></span>  
 <span data-ttu-id="6ed83-120">定義繫結延伸模組，用於接收位置或傳送埠 machine.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="6ed83-120">Define the binding extension used in the receive location or send port in machine.config file.</span></span> <span data-ttu-id="6ed83-121">此外，若要取得的自訂行為或繫結項目搭配使用 WCF 自訂配接器，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="6ed83-121">Also, to get a custom behavior or binding element to work with WCF-Custom adapter, complete these steps:</span></span>  
  
1.  <span data-ttu-id="6ed83-122">GAC 組件</span><span class="sxs-lookup"><span data-stu-id="6ed83-122">GAC the assembly</span></span>  
  
2.  <span data-ttu-id="6ed83-123">修改 machine.config 檔案 (位於**%FrameworkDir%\v4.0.30319\CONFIG**)。</span><span class="sxs-lookup"><span data-stu-id="6ed83-123">Modify your machine.config file (found in **%FrameworkDir%\v4.0.30319\CONFIG**).</span></span>  
  
    1.  <span data-ttu-id="6ed83-124">載入您的行為 DLL 內 服務組態編輯器 (**svcConfigEditor.exe**)。</span><span class="sxs-lookup"><span data-stu-id="6ed83-124">Load your behavior DLL inside the Service Configuration Editor (**svcConfigEditor.exe**).</span></span>  
  
    2.  <span data-ttu-id="6ed83-125">儲存設定到**app.config**檔案</span><span class="sxs-lookup"><span data-stu-id="6ed83-125">Save the configuration to an **app.config** file</span></span>  
  
    3.  <span data-ttu-id="6ed83-126">複製並貼上**system.servicemodel** machine.config 中的類似一節中的延伸模組 > 一節。如果**system.servicemodel**區段沒有出現在 machine.config 中，您必須建立一個。</span><span class="sxs-lookup"><span data-stu-id="6ed83-126">Copy and paste the **system.servicemodel** extensions section in a similar section in machine.config. If **system.servicemodel** section is not present in machine.config, your must create one.</span></span> <span data-ttu-id="6ed83-127">Machine.config 檔案的組態區段的範例如下：</span><span class="sxs-lookup"><span data-stu-id="6ed83-127">The following is an example from the configuration section of a machine.config file:</span></span>  
  
        ```  
          <system.serviceModel>  
            <extensions>  
              <behaviorExtensions>  
                <add name="BizTalkWcfContractNamespaceTestServiceBehaviorExtension" type="ASB.BizTalk.Samples.BizTalkWcfContractNamespaceTestServiceBehaviorExtension, CustomBizTalkWcfBehaviors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=7631521c07cf34b4" />  
              </behaviorExtensions>  
            </extensions>  
          </system.serviceModel>  
        ```  
  
> [!NOTE]
>  <span data-ttu-id="6ed83-128">上述程式碼也可以加入 [WCF 延伸模組] 索引標籤。如果延伸模組必須在接收端，請參閱**\<主機名稱\>屬性對話方塊、 WCF 延伸模組** 索引標籤 （Wcf-custom 或 Wcf-customisolated 配接器接收處理常式） [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="6ed83-128">The above code can also be added to the WCF Extensions tab. If the extension needs to be on the receive side, see the **\<Host Name\> Properties Dialog Box, WCF Extensions** tab (WCF-Custom or WCF-CustomIsolated Adapter Receive Handler) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> <span data-ttu-id="6ed83-129">如果延伸模組必須在傳送端，請參閱**\<主機名稱\>屬性對話方塊、 WCF 延伸模組** 索引標籤 （Wcf-custom 配接器傳送處理常式） [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="6ed83-129">If the extension needs to be on the send side, see **\<Host Name\> Properties Dialog Box, WCF Extensions** tab (WCF-Custom Adapter Send Handler) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>  
  
 3. <span data-ttu-id="6ed83-130">關閉並重新開啟您的系統管理員主控台。</span><span class="sxs-lookup"><span data-stu-id="6ed83-130">Close and reopen your admin console.</span></span> <span data-ttu-id="6ed83-131">您應該可以看到您的自訂行為，Wcf-custom 配接器中，連接埠應保持在啟用狀態時啟用它。</span><span class="sxs-lookup"><span data-stu-id="6ed83-131">You should be able to see your custom behavior in the WCF-Custom adapter, and the port should stay enabled when you enable it.</span></span>