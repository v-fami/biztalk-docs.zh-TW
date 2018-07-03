---
title: 無效的服務憑證指紋 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 22e7d74e-40ec-4187-9246-bc8da2a9ce86
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5dcd37c3f3f2d56a9bdc2c576fee344a0eef7df4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005144"
---
# <a name="invalid-service-certificate-thumbprint"></a>無效的服務憑證指紋
## <a name="details"></a>詳細資料  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  產品名稱   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| 產品版本 |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    事件識別碼     |                                         0                                          |
|  事件來源   |                                         0                                          |
|    元件    |                                         0                                          |
|  符號名稱  |                                         0                                          |
|  訊息文字   |       無效的服務憑證指紋;必須是 40 位數的十六進位數字       |
  
## <a name="explanation"></a>說明  
 指定無效的服務憑證指紋。  
  
## <a name="user-action"></a>使用者動作  
 在程式碼中設定 WCF 連接埠，使用者介面的服務憑證屬性應為十六進位的 40 位數值。 範例： 798A68E7A3E6F2CCC6929FC4AF2A15A9EED66E39  
  
 如需有關憑證的詳細資訊，請參閱下列資源：  
  
-   [安裝 WCF 配接器的憑證](../core/installing-certificates-for-the-wcf-adapters.md)