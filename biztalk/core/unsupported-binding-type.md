---
title: 不支援的繫結類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5556a7d7-f092-4f69-9561-88f51ac46cc9
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a1090157a3b39dea62a3c95cb787b91e0a33bfc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004335"
---
# <a name="unsupported-binding-type"></a>不支援的繫結類型
## <a name="details"></a>詳細資料  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  產品名稱   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| 產品版本 |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    事件識別碼     |                                         0                                          |
|  事件來源   |                                         0                                          |
|    元件    |                                         0                                          |
|  符號名稱  |                                         0                                          |
|  訊息文字   |                              不支援的繫結類型                              |
  
## <a name="explanation"></a>說明  
 已選擇 MsmqIntegration 繫結，但是這不受 WCF 配接卡支援。  
  
## <a name="user-action"></a>使用者動作  
 使用 WCF-NetMsmq 配接器。 如果需要交換原生的 MSMQ 訊息，請使用 BizTalk MSMQ 配接器。  
  
 如需設定配接器的詳細資訊，請參閱下列資源：  
  
-   [設定 WCF-NetMsmq 配接器](../core/configuring-the-wcf-netmsmq-adapter.md)