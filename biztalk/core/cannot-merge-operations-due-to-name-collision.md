---
title: 無法合併作業，因為名稱衝突 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81ddb8b7-6f7e-420c-b7c3-921c0e305326
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57bbb3b085af45ede5632e20f67d5e6c0c4e304e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992319"
---
# <a name="cannot-merge-operations-due-to-name-collision"></a>無法合併作業，因為名稱衝突
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                             |
|-----------------|-------------------------------------------------------------------------------------------------------------|
|  產品名稱   |             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]              |
| 產品版本 |                         [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                          |
|    事件識別碼     |                                                      0                                                      |
|  事件來源   |                                                      0                                                      |
|    元件    |                                                      0                                                      |
|  符號名稱  |                                                      0                                                      |
|  訊息文字   | 無法合併作業 「{0}"因為名稱衝突。 Web 服務中的所有作業必須都有唯一的名稱。 |
  
## <a name="explanation"></a>說明  
 此錯誤表示的連接埠名稱或作業名稱的兩個不同的連接埠正在合併具有相同的名稱。  
  
## <a name="user-action"></a>使用者動作  
 使用連接埠組態精靈，請確定正在進行合併的所有連接埠有不同的連接埠名稱和作業。  
  
 如需有關通訊埠組態的詳細資訊，請參閱下列資源中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  
  
-   [如何執行連接埠組態精靈](../core/how-to-run-the-port-configuration-wizard.md)