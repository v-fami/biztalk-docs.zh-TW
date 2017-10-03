---
title: "ExportSettings 命令 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa34dab1-c854-473e-a693-43ba45624e16
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab8c39ef6903affbd2a1446bbde18a56e1a7778c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="exportsettings-command"></a>ExportSettings 命令
ExportSettings 指令碼可讓您將 BizTalk Server 組態資料庫中的 BizTalk Server 設定匯出至 XML 檔案。 您可以再匯入另一個環境中的這些設定中所述[如何匯入 BizTalk 設定使用設定儀表板](../core/how-to-import-biztalk-settings-using-settings-dashboard.md)或[如何使用 BTSTask 匯入 BizTalk 設定](../core/how-to-import-biztalk-settings-using-btstask.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此作業，您必須以 BizTalk Server Administrators 群組的成員身分登入。  
  
## <a name="usage"></a>使用方式  
 `ExportSettings –Destination:value[-Server:value] [-Database:value]`  
  
## <a name="parameters"></a>參數  
  
|**參數**|Required|值|  
|-------------------|--------------|-----------|  
|**目的端**|是|要寫入之 XML 檔案的路徑和檔案名稱。|  
|**伺服器**|選擇性|裝載 BizTalk 組態資料庫的 SQL 伺服器名稱。|  
|**資料庫**|選擇性|BizTalk 組態資料庫的名稱。|  
  
## <a name="sample"></a>範例  
 `BTSTask ExportSettings /Destination:MyFile.xml /Server:MyServer /Database:MyMgmtDb`  
  
## <a name="remarks"></a>備註  
 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
## <a name="see-also"></a>另請參閱  
 [BTSTask 命令列參考](../core/btstask-command-line-reference.md)