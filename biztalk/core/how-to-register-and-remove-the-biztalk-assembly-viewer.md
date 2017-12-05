---
title: "如何註冊和移除 BizTalk 組件檢視器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f80b906-0a9e-4bcd-984d-db4550f2e51f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ad3628f61fec11f135bf2235f5e0d25f52992d3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-register-and-remove-the-biztalk-assembly-viewer"></a>如何註冊和移除 BizTalk 組件檢視工具
在 BizTalk Server 安裝期間，不會自動註冊 BizTalk「組件檢視工具」。 若要註冊或移除 BizTalk「組件檢視工具」，請執行下列步驟。  
  
### <a name="to-add-assembly-viewer-to-the-windows-registry"></a>若要將組件檢視工具加入至 Windows 登錄  
  
1.  從**啟動**功能表上，按一下 **執行**。  
  
2.  在 [執行] 對話方塊中，輸入**cmd**。  
  
3.  從命令列中，瀏覽至\< *BizTalk Server 安裝資料夾*\>\Developer Tools\ 目錄所在的位置。  
  
4.  在命令列輸入：  
  
     regsvr32 BTSAsmExt.dll  
  
5.  若要開始使用「組件檢視工具」，請登出然後再登入電腦。  
  
### <a name="to-remove-assembly-viewer-from-the-windows-registry"></a>若要從 Windows 登錄中移除組件檢視工具  
  
1.  從**啟動**功能表上，按一下 **執行**。  
  
2.  在**執行** 對話方塊中，輸入**cmd**。  
  
3.  從命令列中，瀏覽至\< *BizTalk Server 安裝資料夾*\>\Developer Tools\ 目錄所在的位置。  
  
4.  在命令列輸入：  
  
     regsvr32/u BTSAsmExt.dll  
  
5.  若要完成移除，請登出然後再登入電腦。  
  
## <a name="see-also"></a>請參閱  
 [使用 BizTalk 組件檢視工具檢視組件](../core/viewing-assemblies-with-the-biztalk-assembly-viewer.md)