---
title: ImportSettings 命令 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 587f7e1f-9cf7-4e7b-90cd-11a266f474dc
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c609634422f8c8b5f2c1a96691fe4eda708e5c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257550"
---
# <a name="importsettings-command"></a>ImportSettings 命令
從來源 XML 檔案將 BizTalk 群組、主控件或主控件執行個體設定匯入組態資料庫。 設定在匯入對應的 XML 檔案中後會進行對應。 這些設定可能是已匯出中所述[匯入或匯出 BizTalk 設定使用設定儀表板](how-to-import-biztalk-settings-using-settings-dashboard.md)或[匯入或匯出 BizTalk 設定使用 BTSTask](how-to-import-biztalk-settings-using-btstask.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這項作業，您必須為 BizTalk Server 系統管理員群組的成員登入。  
  
## <a name="usage"></a>使用方式  
 `ImportSettings –Source:value –Map: value [-Server:value] [-Database:value]`  
  
## <a name="parameters"></a>參數  
  
|**參數**|Required|值|  
|-------------------|--------------|-----------|  
|**原始碼**|是|匯出的設定 XML 檔案的路徑與檔案名稱。|  
|**-對應**|是|對應的設定 XML 檔案的路徑與檔案名稱。|  
|**伺服器**|選擇性|裝載 BizTalk 組態資料庫的 SQL Server 電腦名稱。|  
|**資料庫**|選擇性|BizTalk 組態資料庫的名稱。|  
  
## <a name="sample"></a>範例  
 `BTSTask ImportSettings /Source:”C:\My Folder>\ExportedSettings.xml” /Map:Mappings.xml /Server:MyServer /Database:MyMgmtDb`  
  
## <a name="remarks"></a>備註  
 參數不區分大小寫。 您不需要輸入整個參數名稱來指定它；您可以輸入參數名稱的前幾個字母，只要能明確識別就好了。  
  
## <a name="see-also"></a>另請參閱  
 [BTSTask 命令列參考](../core/btstask-command-line-reference.md)