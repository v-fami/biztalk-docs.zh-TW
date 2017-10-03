---
title: "驗證收到的 EDI 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c56a3c0-042e-4611-8131-d51098064f0f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dcc48b343332ea6b402841ec5ed1f5c9af49b2dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="validation-of-received-edi-messages"></a>驗證已接收的 EDI 訊息
EDI 接收管線處理內送訊息時，會對信封和訊息資料執行一系列驗證。 有些驗證處理是固定會執行的，而有些需經啟用才會執行。 這些驗證包括下列項目：  
  
-   **一律會執行驗證都**:  
  
    -   驗證交換信封的結構。  
  
    -   根據交易夥伴協議 (若未定義協議，則根據後援協議) 對信封執行的驗證。  
  
    -   對信封和控制結構描執行的結構描述驗證。  
  
    -   對交易集資料元素和訊息結構描述執行的結構描述驗證。  
  
    -   根據 X12 標準所提供的「交易集-群組」對應，對單一群組內的交易集類型執行的驗證。  
  
-   **啟用時，才會執行驗證都**:  
  
    -   對交易集資料項目執行的 EDI 驗證。 需在協議屬性中啟用才會執行。  
  
    -   對交易集資料元素執行的擴充驗證。 需在協議屬性中啟用才會執行。  
  
    -   交易集資料項目的欄位交互驗證 (僅限 X12 編碼訊息)。 需在訊息結構描述中啟用才會執行。  
  
## <a name="see-also"></a>另請參閱  
 [EDI 結構驗證](../core/edi-structural-validation.md)   
 [協議屬性驗證](../core/agreement-properties-validation.md)   
 [EDI 類型 （資料元素） 驗證](../core/edi-type-data-element-validation.md)   
 [擴充 (BTS-XSD) 驗證](../core/extended-bts-xsd-validation.md)   
 [結構描述驗證](../core/schema-validation2.md)   
 [交叉驗證欄位區段](../core/cross-field-segment-validation.md)