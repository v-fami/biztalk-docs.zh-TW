---
title: 如何建立分支機構應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3be483f8-2617-459e-9081-aab886c75d93
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 5145111b2c585edab92cc10c3e3614e8bb91a85d
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-create-an-affiliate-application"></a>如何建立分支機構應用程式
您可以使用 MMC 嵌入式管理單元或**createapps**來建立一或多個應用程式，如 XML 檔案所指定的命令。 以下是範例 XML 檔案的 Windows-Initiated 單一登入 (SSO):  
  
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
  
-   分支機構應用程式的名稱。  
  
-   分支機構應用程式相關聯的欄位。  
  
-   分支機構應用程式類型 （主機群組、 個別或組態存放區）。  
  
-   與分支機構系統管理員群組相同的管理帳戶。 （指定這個旗標會永遠使用分支機構系統管理員群組做為系統管理員帳戶進行此分支機構應用程式）。  
  
> [!IMPORTANT]
>  您可以將 allowLocalAccounts 旗標設為 [是]，以使用系統管理員帳戶和使用者帳戶的本機帳戶。 不過，您應該只在單一電腦的情況下使用這個旗標。  
  
> [!IMPORTANT]
>  您必須是 SSO 系統管理員或 SSO 分支機構系統管理員，才能執行這項工作。  
  
> [!NOTE]
>  如果您網域控制站上執行設定時，網域本機領域群組指定應用程式系統管理員或應用程式使用者建立分支機構應用程式時，建議您啟用的本機帳戶旗標。 若要這樣做：  
  
-   在 MMC 嵌入式管理單元中，選取 允許本機帳戶作為存取帳戶建立過程。  
  
-   從命令列指定 allowLocalAccounts = 分支機構應用程式建立的 XML 檔案中的 [是]。  
  
 建立分支機構應用程式後，您必須啟用它。 如需詳細資訊，請參閱[如何啟用分支機構應用程式](../esso/how-to-enable-an-affiliate-application.md)。  
  
### <a name="to-create-an-affiliate-application-using-the-microsoft-management-console-mmc-snap-in"></a>若要建立分支機構應用程式使用 Microsoft Management Console (MMC) 嵌入式管理單元  
  
1.  按一下**啟動**，指向 **程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  以滑鼠右鍵按一下**分支機構應用程式**，然後按一下 **新增**。  
  
4.  請依照下列中的指示**建立新的分支機構應用程式**精靈。  
  
### <a name="to-create-an-affiliate-application-using-the-command-line"></a>使用命令列建立分支機構應用程式  
  
1.  按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。  
  
2.  在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。  
  
     預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別`ssomanage –createapps <application file name>`，其中*\<應用程式檔案名稱 >*是 XML 檔案。  
  
## <a name="see-also"></a>另請參閱  
 [SSO 分支機構應用程式](../esso/sso-affiliate-applications.md)   
 [如何啟用分支機構應用程式](../esso/how-to-enable-an-affiliate-application.md)   
 [如何刪除分支機構應用程式](../esso/how-to-delete-an-affiliate-application.md)   
 [管理使用者對應](../esso/managing-user-mappings.md)   
 [管理分支機構應用程式](../esso/managing-affiliate-applications.md)