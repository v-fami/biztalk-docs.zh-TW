---
title: 如何建立分支機構應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [SSO applications], creating
- applications [SSO], creating
- creating, applications [SSO]
ms.assetid: d0967c4b-6201-416a-9d3a-23b5de5b83d6
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2f621faef7694a3dba7885bab5641e0baa58e8f
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-create-an-affiliate-application"></a>如何建立分支機構應用程式
您可以使用 MMC 嵌入式管理單元或此命令來建立一或多個應用程式，如 XML 檔案所指定。 Windows 初始化的 SSO 範例 XML 檔案如下：  
  
```  
<sso>  
<application name="SAP">  
<description>The SAP application</description>   
<contact>someone@example.com</contact>   
<appuserAccount>domain\AppUserAccount</appuserAccount>   
<appAdminAccount>domain\AppAdminAccount</appAdminAccount>   
<field ordinal="0" label="User Id" masked="no" />   
<field ordinal="1" label="Password" masked="yes" />   
<flags groupApp="no" configStoreApp="no" allowTickets="no" validateTickets="yes" allowLocalAccounts="no" timeoutTickets="yes" adminAccountSame="no" enableApp="no" />  
</application>  
</sso>  
  
```  
  
 建立分支機構應用程式後，無法修改以下屬性：  
  
-   分支機構應用程式的名稱  
  
-   與分支機構應用程式關聯的欄位  
  
-   分支機構應用程式類型 (主控件群組、個別或組態存放區)  
  
-   與分支機構系統管理員群組相同的管理帳戶。 (指定這個旗標會永遠使用分支機構系統管理員群組做為此分支機構應用程式的系統管理員帳戶)  
  
> [!IMPORTANT]
>  您可以將 allowLocalAccounts 旗標設為 [是]，以使用系統管理員帳戶和使用者帳戶的本機帳戶。 不過，您應該只在單一電腦的情況下使用這個旗標。  
  
> [!IMPORTANT]
>  您必須是 SSO 系統管理員或 SSO 分支機構系統管理員，才能執行這項工作。  
  
 建立分支機構應用程式後，您必須啟用它。 如需詳細資訊，請參閱[如何啟用分支機構應用程式](../core/how-to-enable-an-affiliate-application.md)。  
  
### <a name="to-create-an-affiliate-application-using-the-mmc-snap-in"></a>若要使用 MMC 嵌入式管理單元建立分支機構應用程式  
  
1.  在 **啟動**  功能表上，按一下  **程式**, ，按一下  **Microsoft 企業單一登入**, ，然後按一下  **SSO 管理**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  以滑鼠右鍵按一下 **分支機構應用程式**, ，然後按一下  **建立應用程式**。  
  
4.  依照 **企業單一登入應用程式精靈**。  
  
### <a name="to-create-an-affiliate-application-using-the-command-line"></a>使用命令列建立分支機構應用程式  
  
1.  在 **啟動** ] 功能表上，按一下 [ **執行**, ，然後輸入 **cmd**。  
  
2.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別 * * ssomanage – createapps *\<應用程式檔案名稱\>* * *，其中*\<應用程式檔案名稱\>*是 XML 檔案。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 分支機構應用程式](../core/sso-affiliate-applications.md)   
 [如何啟用分支機構應用程式](../core/how-to-enable-an-affiliate-application.md)   
 [如何刪除分支機構應用程式](../core/how-to-delete-an-affiliate-application.md)   
 [管理使用者對應](../core/managing-user-mappings.md)   
 [管理分支機構應用程式](../core/managing-affiliate-applications.md)