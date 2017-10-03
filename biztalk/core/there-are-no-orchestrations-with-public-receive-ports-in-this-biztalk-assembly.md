---
title: "沒有公開使用沒有協調流程中此 BizTalk 組件的接收埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb901d49-ce3c-4bc6-806a-eb5964d32bb4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e04c10119b617ebabe07169dcae999fe60210e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="there-are-no-orchestrations-with-public-receive-ports-in-this-biztalk-assembly"></a>沒有公開使用沒有協調流程中此 BizTalk 組件的接收埠
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|沒有公開使用沒有協調流程中此 BizTalk 組件的接收埠。 按一下 上一步，指定 BizTalk 組件包含使用公開的協調流程接收埠|  
  
## <a name="explanation"></a>說明  
 此錯誤表示選取的協調流程並沒有公用連接埠。  
  
## <a name="user-action"></a>使用者動作  
 您可以使用下列程序來設定公用連接埠。  
  
#### <a name="to-configure-a-public-port"></a>若要設定公用連接埠  
  
1.  尋找協調流程，並建立所需的接收埠公用。  
  
    1.  開啟連接埠組態精靈。  
  
    2.  在**選取連接埠類型**，變更**存取限制**從**內部**（預設） 加入**公用-沒有限制**。  
  
2.  重新編譯的組件。  
  
     \- 或 -  
  
     載入具有公用的 BizTalk 組件的接收埠。