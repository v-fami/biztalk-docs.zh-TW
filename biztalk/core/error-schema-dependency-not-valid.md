---
title: "錯誤-無效的結構描述相依性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.edit.error.schemaDependencyNotValid
ms.assetid: 431278f0-6cd1-4b3f-8d87-16af4991d354
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36326608f191b520c41cb42890aec029c432fd30
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---schema-dependency-not-valid"></a>錯誤-無效的結構描述相依性
**錯誤碼**  
  
 BEC2009  
  
 **說明**  
  
 所有相依的結構描述 (如在目前結構描述所匯入、包括或重新定義者)，必須新增至此 BizTalk 專案或存在於此專案所參考的組件中。 即使結構描述**匯入**，**包含**，和**重新定義**遠端網站指定結構描述的指示詞必須新增至此 BizTalk 專案。  
  
 **使用者動作**  
  
 使用**加入現有項目**命令**檔案**功能表和 Microsoft® BizTalk® Server 專案，將這個結構描述所依存的所有結構描述新增至 BizTalk 專案的捷徑功能表。 將此類結構描述新增至 BizTalk 專案前，您可能必須將它們從網站下載到本機硬碟。