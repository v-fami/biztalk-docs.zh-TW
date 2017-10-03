---
title: "錯誤-表格迴圈運算質不是有效的第一個輸入 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.firstInputForTableLoopingNotValid
ms.assetid: 3ece2c0c-bcac-42d5-9536-34f073937879
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2cfa89175d566ed152caa852dfc7aef2b435447
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---first-input-to-table-looping-functoid-not-valid"></a>錯誤-表格迴圈運算質不是有效的第一個輸入
**錯誤碼**  
  
 btm1071  
  
 **說明**  
  
 第一個輸入的參數相關**表格迴圈**運算質不正確。 這個參數必須是來自來源結構描述中節點的連結，輸入執行個體訊息中的對應元素的發生次數會控制的一組相關聯的次數**表格抽選程式**運算質將會在執行階段叫用。  
  
 **使用者動作**  
  
 請確定輸入的參數**表格迴圈**運算質，透過 **輸入參數**屬性和**設定\<運算質 > 運算質**對話方塊中，您可以在下表所示。  
  
|「表格迴圈」運算質輸入參數編號|Description|  
|---------------------------------------------------|-----------------|  
|1|輸入執行個體訊息從一筆記錄的連結或來源結構描述中的欄位，其中發生次數控制的一組相關聯的次數**表格抽選程式**運算質會執行。|  
|2|透過設定資料表中的資料行數目**表格迴圈格線**屬性之相關**表格迴圈**運算質。|  
|3 – 100|常數與連結 (來自來源結構描述或其他運算質的輸出)，它們將會成為表格迴圈格線的可能資料來源。|