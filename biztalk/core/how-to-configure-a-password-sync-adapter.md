---
title: "如何設定密碼同步配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0effdc9b-4aee-4674-90c5-03dfd7cc4cd6
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f0be0146e905ef291942bd30adc111eff89e989
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-password-sync-adapter"></a><span data-ttu-id="816c6-102">如何設定密碼同步配接器</span><span class="sxs-lookup"><span data-stu-id="816c6-102">How to Configure a Password Sync Adapter</span></span>
<span data-ttu-id="816c6-103">完成建立密碼同步配接器之後，必須將配接器載入系統。</span><span class="sxs-lookup"><span data-stu-id="816c6-103">After you have finished creating your password sync adapter, you must load your adapter on to a system.</span></span> <span data-ttu-id="816c6-104">此外，必須通知「企業單一登入」(ENTSSO) 和組態存放區，您的應用程式為密碼同步配接器。</span><span class="sxs-lookup"><span data-stu-id="816c6-104">Additionally, you must inform Enterprise Single Sign-On (ENTSSO) and the configuration store that your application is a password sync adapter.</span></span> <span data-ttu-id="816c6-105">您必須向組態存放區，基於安全性考量： 您的配接器將會要求更新密碼與其他認證。</span><span class="sxs-lookup"><span data-stu-id="816c6-105">You must register with the configuration store for security purposes: your adapter will request updates to passwords and other credentials.</span></span> <span data-ttu-id="816c6-106">因此，ENTSSO 必須知道是否已允許指定的配接器要求這類權限。</span><span class="sxs-lookup"><span data-stu-id="816c6-106">Therefore, ENTSSO must know that a given adapter is allowed to ask for such permissions.</span></span>  
  
### <a name="to-configure-a-password-sync-adapter"></a><span data-ttu-id="816c6-107">設定密碼同步配接器</span><span class="sxs-lookup"><span data-stu-id="816c6-107">To configure a password sync adapter</span></span>  
  
1.  <span data-ttu-id="816c6-108">使用 SSOPS 工具建立具有組態存放區的配接器。</span><span class="sxs-lookup"><span data-stu-id="816c6-108">Create your adapter with the configuration store using the ssops tool.</span></span>  
  
     <span data-ttu-id="816c6-109">使用 SSOPS 將 XML 組態檔載入組態資料庫，該資料庫會向「企業單一登入」描述您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="816c6-109">Using ssops, you load an XML configuration file into the configuration database that describes your application to Enterprise Single Sign-On.</span></span>  
  
2.  <span data-ttu-id="816c6-110">在建立具有組態資料庫的配接器之後，您可以使用 `ISSOPSAdmin.SetAdapterProperties` 來修改配接器資訊。</span><span class="sxs-lookup"><span data-stu-id="816c6-110">After you create the adapter with the config database, you can modify the adapter information with `ISSOPSAdmin.SetAdapterProperties`.</span></span>  
  
     <span data-ttu-id="816c6-111">雖然這兩個方法很相似，不過 `SetAdapterProperties` 會在組態資訊變更時傳送訊息至配接器。</span><span class="sxs-lookup"><span data-stu-id="816c6-111">While the two methods are similar, `SetAdapterProperties` sends a message to the adapter when the configuration information changes.</span></span>  
  
3.  <span data-ttu-id="816c6-112">若要刪除配接器，可使用 ISSOAdmin.DeleteApplication。</span><span class="sxs-lookup"><span data-stu-id="816c6-112">To delete an adapter, use ISSOAdmin.DeleteApplication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="816c6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="816c6-113">See Also</span></span>  
 [<span data-ttu-id="816c6-114">同步處理密碼</span><span class="sxs-lookup"><span data-stu-id="816c6-114">Synchronizing Passwords</span></span>](../core/synchronizing-passwords.md)