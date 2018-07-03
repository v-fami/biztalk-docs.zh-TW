---
title: 日期和時間運算質 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2e2d49f5-1aaf-4e4d-8da1-e8605304dccb
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5224c409a6d705806cccc493009ce2c32062f0a1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010663"
---
# <a name="date-and-time-functoids"></a>日期和時間運算質

## <a name="overview"></a>概觀
**日期 / 時間**運算質可分為兩類。 第一個類別包含單一運算質**加上天數**，用來將指定的天數新增至指定的日期和時間值。 在輸出執行個體訊息未來應該會加入預估日期和時間時，這類運算質相當有用。 例如，**加上天數**運算質可以用來產生估計出貨日期，根據從收到訂單日期的固定的差異。  

 第二個類別包含所有中的其餘運算質**日期和時間**類別目錄。 它們可提供時間戳記在執行階段，以便可以在輸出執行個體訊息中包含的日期和時間在哪一個訊息執行轉換。  

 **加上天數**運算質接受兩個輸入參數，而**日期**，**日期和時間**，以及**時間**運算質有沒有輸入參數。  

## <a name="available-functoids"></a>可用的運算質  
 **日期 / 時間**運算質為： 

* 加上天數
* date
* 日期及時間
* Time

更多有關這些運算質可**運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。

## <a name="see-also"></a>另請參閱  
- [如何新增基本運算質至對應](../core/how-to-add-basic-functoids-to-a-map.md)   
- **日期和時間運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
