---
title: 設定環境 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 43027efc-acec-4110-96bd-cc4a19daaeab
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f0c63671833a394e0c750561d90c12c6476515f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25961892"
---
# <a name="setting-the-environment"></a>設定環境
**若要設定的環境：**  
  
1.  請確定 SWIFT 訊息組件設定。 請參閱 Swift Message Pack 文件，以設定相同。  
  
2.  執行 SQL 指令碼*\<磁碟機\>*: \Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools\DataImport\CreateProceduresScript.sql。 如果 Swift 和 MessagePack A4Swift 以外的資料庫名稱的設定，變更的 sql 指令碼中的資料庫名稱。  
  
3.  「 資料來源 」 的索引鍵的值設定為電腦名稱和索引鍵做為資料庫名稱的 「 資料庫 」 (為其設定 Swift 與 MessagePack) 檔案中*\<磁碟機\>*: \Program Files\Microsoft BizTalkAccelerator for SWIFT\SDK\Tools\DataImport\DataImport.exe.config。  
  
    > [!NOTE]
    >  資料輸入的檔案不應該為 DataImport.exe 檔案的相同資料夾中。  
  
4.  執行 DataImport 公用程式匯入 BICplusIBAN 和 SEPA 資料表中的資料。