---
title: 協調流程沒有公用接收埠，此 BizTalk 組件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb901d49-ce3c-4bc6-806a-eb5964d32bb4
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c062f5e23972ed841c4c9d614ad58967a07a4fe2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978213"
---
# <a name="there-are-no-orchestrations-with-public-receive-ports-in-this-biztalk-assembly"></a>協調流程沒有公用接收埠，此 BizTalk 組件
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                               |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                               |
| 產品版本 |                                                          [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                           |
|    事件識別碼     |                                                                                       0                                                                                       |
|  事件來源   |                                                                                       0                                                                                       |
|    元件    |                                                                                       0                                                                                       |
|  符號名稱  |                                                                                       0                                                                                       |
|  訊息文字   | 協調流程沒有公用接收埠，在此 BizTalk 組件中。 按一下 [上一頁] 並指定包含具有公用的協調流程的 BizTalk 組件的接收埠 |
  
## <a name="explanation"></a>說明  
 此錯誤表示選取的協調流程沒有公用連接埠。  
  
## <a name="user-action"></a>使用者動作  
 您可以使用下列程序來設定公用連接埠。  
  
#### <a name="to-configure-a-public-port"></a>若要設定的公用連接埠  
  
1.  尋找協調流程，並公開所需的接收埠。  
  
    1.  開啟連接埠組態精靈。  
  
    2.  在 **選取連接埠類型**，變更**存取限制**從**內部**（預設） 加入**公用-沒有限制**。  
  
2.  重新編譯組件。  
  
     \- 或 -  
  
     載入 BizTalk 組件具有公用接收埠。