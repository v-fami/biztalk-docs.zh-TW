---
title: "錯誤-從不同的父記錄輸入累計運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.inputsToCumulativeFromDiffParents
ms.assetid: a2dcfe6f-0cd4-41ed-a69f-e510a74760a9
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3c919001e05ca99383ffce72c8d450f6d04624b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---inputs-to-cumulative-functoid-from-different-parent-records"></a>錯誤-從不同的父記錄輸入累計運算質
**錯誤碼**  
  
 btm1032  
  
 **說明**  
  
 為指定**累計**運算質，第二個輸入的參數 （累積範圍） 是來自來源結構描述的節點做為第一個輸入參數 （要累計的節點） 的不同部分。  
  
 **使用者動作**  
  
 請確定這兩個輸入參數來指定**累計**運算質會共用相同的父記錄，或您提供第二個輸入的參數 （累積範圍） 具有常數輸入的參數。