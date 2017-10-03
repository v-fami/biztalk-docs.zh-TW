---
title: "如何停用 SSO |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disabling, SSO
- SSO, disabling
- managing [SSO], disabling
ms.assetid: 0fe4f87a-d7c2-4af6-afee-1065bc4a5285
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c8069ffb291b64d832a1d3ce483e7ab09be655f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-disable-sso"></a>如何停用 SSO
您可以使用 MMC 嵌入式管理單元或是命令列，以停用整個「單一登入」系統。  
  
 停用所有「單一登入伺服器」時將會有短暫的延遲，因為它們會輪詢 SSO 資料庫是否有最新的全域資訊。  
  
### <a name="to-disable-enterprise-single-sign-on-using-the-mmc-snap-in"></a>使用 MMC 嵌入式管理單元停用企業單一登入  
  
1.  在 **[開始]** 功能表上，依序按一下 **[所有程式]**及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  以滑鼠右鍵按一下**系統**，然後按一下 **停用**。  
  
### <a name="to-disable-enterprise-single-sign-on-using-the-command-line"></a>使用命令列停用企業單一登入  
  
1.  在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。  
  
2.  在命令列提示字元中，移至「企業單一登入」安裝目錄。 預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssomanage – disablesso**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>另請參閱  
 [如何啟用 SSO](../core/how-to-enable-sso.md)   
 [使用 SSO](../core/using-sso.md)