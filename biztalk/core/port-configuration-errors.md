---
title: 連接埠組態錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92eae0d8-a0c4-4f8c-b91a-fd98b9f6931a
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8cc3c8763115e93387bed5195f234bf4a070b9b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986903"
---
# <a name="port-configuration-errors"></a>連接埠組態錯誤
診斷及解決 WCF 通訊埠設定錯誤的資訊。  

## <a name="cannot-merge-operation-due-to-communication-pattern-conflict"></a>無法合併操作，因為通訊模式衝突
  
|                 |                                                         詳細資料                                                         |
|-----------------|-------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                    |
| 產品版本 |                               [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                |
|    事件識別碼     |                                                            0                                                            |
|  事件來源   |                                                            0                                                            |
|    元件    |                                                            0                                                            |
|  符號名稱  |                                                            0                                                            |
|  訊息文字   | 無法合併作業 「{0}「 因為通訊模式衝突。  所有作業必須都為單向或要求-回應 |
  
### <a name="explanation"></a>說明  
 此錯誤表示[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]嘗試合併具有不同的通訊模式的連接埠類型的連接埠。  
  
### <a name="user-action"></a>使用者動作  
 使用連接埠組態精靈 中，請確定正在進行合併的所有連接埠有相同的通訊方向可能是單向或要求-回應。  
  
 如需有關通訊埠組態的詳細資訊，請參閱[如何執行連接埠組態精靈](../core/how-to-run-the-port-configuration-wizard.md)。
 
## <a name="port-types-that-have-a-combination-of-one-way-and-request-response-operations-are-not-allowed"></a>連接埠類型具有多種單向和要求-回應作業不允許 
  
|                 |                                                                                詳細資料                                                                                |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                          [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                           |
| 產品版本 |                                                      [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                       |
|    事件識別碼     |                                                                                   0                                                                                   |
|  事件來源   |                                                                                   0                                                                                   |
|    元件    |                                                                                   0                                                                                   |
|  符號名稱  |                                                                                   0                                                                                   |
|  訊息文字   | 連接埠類型具有多種單向和要求-回應作業不允許。 更正服務描述"{0}「 連接埠類型 」{1}"，然後重新執行精靈 |
  
### <a name="explanation"></a>說明  
 此錯誤表示嘗試取用的服務有單向和雙向作業 （或要求-回應）。  
  
### <a name="user-action"></a>使用者動作  
 更正服務與適當的作業 (可能是單向或要求-回應但非兩者) 並嘗試使用 （如果您擁有想要使用的 WCF 服務時）。 否則，請連絡服務提供者。
