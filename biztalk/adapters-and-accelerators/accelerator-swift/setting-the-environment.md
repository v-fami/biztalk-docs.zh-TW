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
# <a name="setting-the-environment"></a><span data-ttu-id="5dbc5-102">設定環境</span><span class="sxs-lookup"><span data-stu-id="5dbc5-102">Setting the Environment</span></span>
<span data-ttu-id="5dbc5-103">**若要設定的環境：**</span><span class="sxs-lookup"><span data-stu-id="5dbc5-103">**To set the environment:**</span></span>  
  
1.  <span data-ttu-id="5dbc5-104">請確定 SWIFT 訊息組件設定。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-104">Make sure SWIFT Message Pack is configured.</span></span> <span data-ttu-id="5dbc5-105">請參閱 Swift Message Pack 文件，以設定相同。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-105">Refer to the Swift Message Pack documentation to configure the same.</span></span>  
  
2.  <span data-ttu-id="5dbc5-106">執行 SQL 指令碼*\<磁碟機\>*: \Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools\DataImport\CreateProceduresScript.sql。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-106">Run the SQL script *\<drive\>*:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools\DataImport\CreateProceduresScript.sql.</span></span> <span data-ttu-id="5dbc5-107">如果 Swift 和 MessagePack A4Swift 以外的資料庫名稱的設定，變更的 sql 指令碼中的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-107">Change the database name in the sql script if the Swift and MessagePack are configured for database name other than A4Swift.</span></span>  
  
3.  <span data-ttu-id="5dbc5-108">「 資料來源 」 的索引鍵的值設定為電腦名稱和索引鍵做為資料庫名稱的 「 資料庫 」 (為其設定 Swift 與 MessagePack) 檔案中*\<磁碟機\>*: \Program Files\Microsoft BizTalkAccelerator for SWIFT\SDK\Tools\DataImport\DataImport.exe.config。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-108">Set the value of Key “datasource” as ComputerName and key “database” as database name (for which the Swift and MessagePack is configured) in the file *\<drive\>*:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tools\DataImport\DataImport.exe.config.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5dbc5-109">資料輸入的檔案不應該為 DataImport.exe 檔案的相同資料夾中。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-109">The data input file should not be in the same folder as the DataImport.exe file.</span></span>  
  
4.  <span data-ttu-id="5dbc5-110">執行 DataImport 公用程式匯入 BICplusIBAN 和 SEPA 資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="5dbc5-110">Run the DataImport utility to import data in BICplusIBAN and SEPA tables.</span></span>