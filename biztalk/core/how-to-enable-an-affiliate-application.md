---
title: 如何啟用分支機構應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications [SSO], enabling
- managing [SSO applications], enabling
- enabling, applications [SSO]
ms.assetid: 81c94e1b-cd3d-482e-9a78-9b1476af9e5f
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb36c7c8d083cb72cd92cc90c088c7d8a35a9731
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004191"
---
# <a name="how-to-enable-an-affiliate-application"></a>如何啟用分支機構應用程式
您可以使用 MMC 嵌入式管理單元或命令列，啟用指定的分支機構應用程式。  
  
### <a name="to-enable-an-affiliate-application-using-the-mmc-snap-in"></a>若要使用 MMC 嵌入式管理單元啟用分支機構應用程式  
  
1.  在 **[開始]** 功能表上，依序按一下 **[所有程式]** 及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  以滑鼠右鍵按一下分支機構應用程式，然後按一下**啟用**。  
  
### <a name="to-enable-an-affiliate-application-using-the-command-line"></a>若要啟用分支機構應用程式使用命令列  
  
1. 在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。  
  
2. 在命令列，移至「企業單一登入」安裝目錄。 預設的安裝目錄\<*磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3. 型別<strong>ssomanage-enableapp *\<應用程式名稱\></strong><em>，其中\<</em>應用程式名稱*\>的名稱您想要啟用分支機構應用程式。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 分支機構應用程式](../core/sso-affiliate-applications.md)   
 [如何建立分支機構應用程式](../core/how-to-create-an-affiliate-application.md)   
 [管理使用者對應](../core/managing-user-mappings.md)   
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)