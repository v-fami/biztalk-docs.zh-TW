---
title: "如何啟用 Analysis Services 與 BAM 主要匯入資料庫之間的加密 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Analysis Services, enabling encryption
- Primary Import database [BAM], SQL Server Analysis Services
- Primary Import database [BAM], enabling encryption
- SQL Server Analysis Services, Primary Import database [BAM]
ms.assetid: 8107c557-e57c-4569-9ff7-abcb7a8e5243
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61784be74d93753b8c3ca8ecf7302c6517a1d9c4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-enable-encryption-between-analysis-services-and-the-bam-primary-import-database"></a>如何啟用 Analysis Services 與 BAM 主要匯入資料庫之間的加密
安裝或升級 BAM 期間，預設不會啟用加密。 若要啟用加密，您必須將 BAM 組態 XML 檔案中 UseEncryption 旗標的值設定為 1。  
  
 此外，您也必須啟用 SQL Server Analysis Services 中的加密。 如需有關啟用加密的詳細資訊，請參閱[保護與 Analysis Services 執行個體的用戶端通訊](http://go.microsoft.com/fwlink/?LinkId=190805)(http://go.microsoft.com/fwlink/?LinkId=190805)。  
  
### <a name="to-enable-encryption-between-sql-server-analysis-services-and-the-bam-primary-import-database"></a>啟用 SQL Server Analysis Services 與 BAM 主要匯入資料庫之間的加密  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2.  瀏覽至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]。  
  
3.  型別**bm get-config-FileName:\<輸出檔\>**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
4.  按 ENTER 鍵。  
  
5.  使用文字編輯器開啟您所匯出的組態檔案，並將 UseEncryption 屬性旗標的值變更為 1。  
  
    -   預設值：\<屬性名稱 ="UseEncryption"\>0\</Property\>  
  
    -   新的設定：\<屬性名稱 ="UseEncryption"\>1\</Property\>  
  
6.  更新 BAM 組態輸入**bm 更新-config-FileName:\<組態檔\>**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>請參閱  
 [BAM 管理公用程式](../core/bam-management-utility.md)