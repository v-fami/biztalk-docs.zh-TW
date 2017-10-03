---
title: "設定環境 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43027efc-acec-4110-96bd-cc4a19daaeab
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0c91221162cccb7b6821c0edad12f8e76de2f10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="setting-the-environment"></a>設定環境
**若要設定的環境：**  
  
1.  請確定 SWIFT 訊息組件設定。 請參閱 Swift Message Pack 文件，以設定相同。  
  
2.  執行 SQL 指令碼*\<磁碟機 >*: \Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools\DataImport\CreateProceduresScript.sql。 如果 Swift 和 MessagePack A4Swift 以外的資料庫名稱的設定，變更的 sql 指令碼中的資料庫名稱。  
  
3.  「 資料來源 」 的索引鍵的值設定為電腦名稱和索引鍵做為資料庫名稱的 「 資料庫 」 (的 Swift 和 MessagePack 已設定) 檔案中*\<磁碟機 >*: \Program Files\Microsoft BizTalk Accelerator forSWIFT\SDK\Tools\DataImport\DataImport.exe.config。  
  
    > [!NOTE]
    >  資料輸入的檔案不應該為 DataImport.exe 檔案的相同資料夾中。  
  
4.  執行 DataImport 公用程式匯入 BICplusIBAN 和 SEPA 資料表中的資料。