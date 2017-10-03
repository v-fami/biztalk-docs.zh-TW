---
title: "錯誤-表格迴圈運算質沒有目的結構描述連結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.tableLoopingNoLinkToDestSchema
ms.assetid: cf162e6a-5c61-4adc-978b-af641db67ed2
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 329e6670288f05382acf0ea014ba9ae84c4cb645
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---table-looping-functoid-without-link-to-destination-schema"></a>錯誤-表格迴圈運算質沒有目的結構描述連結
**錯誤碼**  
  
 btm1077  
  
 **說明**  
  
 不同於大部分的運算質**表格迴圈**運算質有多個輸出。 所有這些輸出的其中一個必須做為第一個輸入參數個別執行個體的連接**表格抽選程式**運算質。 剩餘的輸出必須連接到**記錄**目的結構描述中的節點 （具有適當的循環設定）。 這個錯誤發生在後續輸出連結**表格迴圈**運算質遺漏。  
  
 **使用者動作**  
  
 拖曳指定**表格迴圈**記錄適當**記錄**建立遺失的連結到目的結構描述的節點。