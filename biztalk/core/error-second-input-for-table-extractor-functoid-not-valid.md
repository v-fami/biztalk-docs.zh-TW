---
title: 錯誤-第二個輸入表格抽選程式運算質未正確 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.secondInputForTableExtractorNotValid
ms.assetid: 099f7374-8625-40af-a74b-24c4de941a7b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e674ad6777ebff53fefe053e1b6af46ebc54ef3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="error---second-input-for-table-extractor-functoid-not-valid"></a>錯誤-第二個輸入表格抽選程式運算質不正確
**錯誤碼**  
  
 btm1073  
  
 **說明**  
  
 第二個輸入參數相關**表格抽選程式**運算質不正確。 這個參數必須是正整數常數，指出有效的資料行中的表格迴圈格線設定**表格迴圈**運算質的第一個輸入參數所指示。  
  
 **使用者動作**  
  
 請確認相關的輸入的參數**表格抽選程式**運算質，透過其**輸入參數**屬性和**設定\<運算質\>運算質**對話方塊中，您可以在下表所示。  
  
|表格擷取程式運算質輸入參數編號|Description|  
|-----------------------------------------------------|-----------------|  
|1|從連結**表格迴圈**從這個運算質**表格抽選程式**依其第二個參數指定運算質會提取資料行的資料。|  
|2|透過設定資料表中的有效資料行數目**表格迴圈格線**屬性**表格迴圈**第一個輸入參數所指定的運算質。|