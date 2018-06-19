---
title: MQSeries 配接器的 XML 組態檔 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, mqsconfigwiz
- configuring [MQSeries adapters], silent configuration
- MQSeries adapters, silent configuration
- configuring [MQSeries adapters], mqsconfigwiz
- mqsconfigwiz [MQSeries adapters]
ms.assetid: 5f19e55c-0f2c-46d7-bb5d-1eb147c296b3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a0356c69b90f0dcfd5fc636b302a97b2de5674b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289766"
---
# <a name="xml-configuration-file-for-the-mqseries-adapter"></a><span data-ttu-id="ffd6d-102">MQSeries 配接器的 XML 組態檔</span><span class="sxs-lookup"><span data-stu-id="ffd6d-102">XML Configuration File for the MQSeries Adapter</span></span>
<span data-ttu-id="ffd6d-103">XML 組態檔讀取**mqsconfigwiz**包含使用者輸入時使用此精靈的 Windows 版本的相同資訊。</span><span class="sxs-lookup"><span data-stu-id="ffd6d-103">The XML configuration file read by **mqsconfigwiz** contains the same information a user enters when using the Windows version of the wizard.</span></span> <span data-ttu-id="ffd6d-104">此資訊會包括應用程式識別，以及使用者識別碼與密碼 (如有需要)、角色名稱和該角色一部分的使用者清單。</span><span class="sxs-lookup"><span data-stu-id="ffd6d-104">This information includes the application identity and the user ID and password if required, the role name, and a list of users who are part of that role.</span></span>  
  
 <span data-ttu-id="ffd6d-105">可能出現的檔案範例如下：</span><span class="sxs-lookup"><span data-stu-id="ffd6d-105">An example of the file might appear as follows:</span></span>  
  
```  
<MQSeriesConfig>  
    <AppIdentity>thisuser</AppIdentity>  
    <userid>domain\username</userid>  
    <password>Bippity.Boppity</password>  
    <rolename>CreatorOwner</rolename>  
    <userlist>  
        <username>domain\user1</username>  
        <username>domain\user2</username>  
    </userlist>  
</MQSeriesConfig>  
```  
  
 <span data-ttu-id="ffd6d-106">您可以使用 **[thisuser]**， **[interactiveuser]**， **LocalService**，或**NetworkService**做為值 **[appidentity]**.</span><span class="sxs-lookup"><span data-stu-id="ffd6d-106">You can use **thisuser**, **InteractiveUser**, **LocalService**, or **NetworkService** as values for **AppIdentity**.</span></span> <span data-ttu-id="ffd6d-107">使用**userid**和**密碼**只具有元素 **[thisuser]**。</span><span class="sxs-lookup"><span data-stu-id="ffd6d-107">Use the **userid** and **password** elements only with **thisuser**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffd6d-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffd6d-108">See Also</span></span>  
 [<span data-ttu-id="ffd6d-109">MQSeries 配接器的無訊息組態</span><span class="sxs-lookup"><span data-stu-id="ffd6d-109">Silent Configuration of the MQSeries Adapter</span></span>](../core/silent-configuration-of-the-mqseries-adapter.md)