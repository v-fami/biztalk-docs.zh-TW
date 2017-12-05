---
title: "升級 BizTalk Accelerator for HL7 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91b6747f-e560-4cf8-99b5-af0d150599bf
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4df85c965943f2f2c916fef6b558f98caf2175f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="upgrade-biztalk-accelerator-for-hl7"></a>升級 BizTalk Accelerator for HL7
概觀[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]升級程序。 
  
<a name="BKMK_BeforeUpgrade"></a>   
## <a name="before-you-upgrade"></a>升級之前  
  
-   執行升級的使用者必須是 BizTalk 系統管理員群組的成員。  
  
-   當您執行升級時，必須執行 SQL Server (MSSQLSERVER) 服務。  
  
-   請勿執行無訊息安裝來升級。  
  
-   當您升級時，安裝程式會移轉現有[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]較新版本的組態資訊。  
  
-   當您升級時，登錄機碼和資料庫會自動備份。  
  
-   中的檔案*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7 資料夾會更新。  
  
> [!IMPORTANT]
>  升級不會建立新的資料夾，針對升級的檔案，也不會改變現有資料夾的名稱。  
  
<a name="BKMK_UpgradePaths"></a>   
## <a name="supported-upgrade-paths"></a>支援的升級路徑  
 下表列出支援[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可以升級的版本。 「 是 」 表示[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]版本可以升級。 「 否 」 表示[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]版本無法升級。 如果[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]版本中沒有列出，該版本無法升級。  

||[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]|[!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)]|BizTalk Server 2013|
|---|---|---|---|  
|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 2013|是|是|否|  
|[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 2010|否|是|是|  

<a name="BKMK_UpgradeSteps"></a>   
## <a name="upgrade-steps"></a>升級步驟  
  
1.  升級[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。   
  
2.  備份[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]資料庫和您 HL7 訊息結構描述。  
  
3.  備份之下任何檔案 ***\<磁碟機\>*: \Program Files\Microsoft BizTalk Accelerator for HL7**已變更的資料夾。 例如，備份 SDK 中的檔案。  
  
4.  安裝適當版本的更新[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]:  
  
    -   如果從 BTAHL7 2010 升級，安裝**HL72010Patch.msp**。  
  
    -   如果從 BTAHL7 2013 升級，安裝**HL72013Patch.msp**。  
    
  
5.  執行[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]安裝程式。 請參閱[安裝 BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md)。  
  
6.  部署新 BTAHL7V2*x*通用專案。  
  
7.  重新部署所有其他組件。  
  
8.  重新建置參考一或多個 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 組件的任何專案或組件。 使用**BTSTask.exe**中\<*磁碟機*\>: \Program Files\Microsoft BizTalk Server\<版本\>，請手動重新部署這些專案。  
  
9. 重新啟動 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 服務。  
  
<a name="BKMK_UpgradeMulti"></a>   
## <a name="upgrading-in-a-multi-server-environment"></a>在多伺服器環境中升級  
 在多伺服器[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]環境，則升級所有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]s，然後再升級[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]所有伺服器上。 請依下列順序移轉您的伺服器：  
  
-   裝載 BizTalk 群組的伺服器  
  
-   每個處理節點  
  
-   BAM 入口網站伺服器  
  
## <a name="see-also"></a>請參閱  
 [安裝 BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md)