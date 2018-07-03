---
title: 如何停用分支機構應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- disabling, applications
- managing [SSO applications], disabling
- applications [SSO], disabling
ms.assetid: febf1687-f0d0-4f87-b462-23535bbddf6d
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8abeb606ea422af4d04ca6e527795d722b58464
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981951"
---
# <a name="how-to-disable-an-affiliate-application"></a>如何停用分支機構應用程式
您可以使用 MMC 嵌入式管理單元或命令列，來停用指定的分支機構應用程式。  
  
### <a name="to-disable-an-affiliate-application-using-the-mmc-snap-in"></a>若要使用 MMC 嵌入式管理單元停用分支機構應用程式  
  
1.  上**開始**功能表上，按一下**程式**，按一下  **Microsoft 企業單一登入**，然後按一下**SSO 管理**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  以滑鼠右鍵按一下分支機構應用程式，然後按一下**停用**。  
  
### <a name="to-disable-an-affiliate-application-using-the-command-line"></a>使用命令列停用分支機構應用程式  
  
1. 按一下 **開始**，按一下**執行**，然後輸入**cmd**。  
  
2. 在命令列，移至「企業單一登入」安裝目錄。 預設的安裝目錄\<*磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3. 型別<strong>ssomanage-disableapp *\<應用程式名稱\></strong><em>，其中\<</em>應用程式名稱*\>名稱分支機構應用程式，您想要停用。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 分支機構應用程式](../core/sso-affiliate-applications.md)   
 [如何啟用分支機構應用程式](../core/how-to-enable-an-affiliate-application.md)   
 [管理使用者對應](../core/managing-user-mappings.md)   
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)