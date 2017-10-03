---
title: "建立分支機構 Applications2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Single Sign-On, creating tickets
- creating affiliate applications
- tickets, SSO
- affiliate applications, enabling XML
- affiliate applications, creating
- SSO tickets
ms.assetid: 95151163-5aaf-4683-afb7-02949ccda3e1
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f39fbbfb62a9081937891b98e2b01a5e7f046e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-affiliate-applications"></a>建立分支機構應用程式
下列步驟說明，如何開始使用分支機構應用程式和單一登入 (SSO)。  
  
> [!NOTE]
>  收到 SSO 錯誤時，請確認您設定 BizTalk Server 時有使用網域帳戶，因為企業單一登入服務的功能會受影響。 SSO 僅能在網域帳戶運作。  
  
### <a name="to-create-an-affiliate-application"></a>若要建立分支機構應用程式  
  
1.  在控制台中開啟**服務**，並確認企業單一登入服務正在執行。  
  
2.  在命令提示中，將目錄變更為 [Enterprise Single Sign-On] 資料夾。  
  
     例如：  
  
     **C:\Program Files\Common Files\Enterprise Single Sign-on >**  
  
3.  使用 [企業單一登入] 命令。 如需命令清單，請使用**-協助**切換。  
  
     ![](../core/media/siebeladapter-23-sso-commands.gif "SiebelAdapter_23_SSO_Commands")  
  
4.  若要使用 *.XML 為啟動程序來建立分支機構應用程式，請輸入下列命令：  
  
     `ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml`  
  
     其中：  
  
    -   C:\SSOtest 是應用程式 XML 所在的資料夾。  
  
    -   AffiliateApplication.xml 就是您建立的應用程式 XML，其中包含登入資訊。  
  
     例如：  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
         <application name="PeopleSoftApp">  
              <description>PeopleSoft SSO Application</description>  
              <contact>someone@microsoft.com</contact>  
             <appUserAccount>DomainName\AppUserGroup</appUserAccount>  
              <!—-an existing group on the domain controller - >   
              <appAdminAccount>DomainName\AppAdminGroup<appAdminAccount>   
              <!-- an existing account in the domain group - >   
              <field ordinal="0" label="User ID" masked="no" />  
              <field ordinal="1" label="Password" masked="yes" />  
              <flags groupApp="no" allowTickets="yes" enableApp="yes"/>  
         </application>  
    </SSO>  
    ```  
  
## <a name="creating-single-sign-on-tickets"></a>建立單一登入票證  
  
#### <a name="to-create-sso-tickets"></a>若要建立 SSO 票證  
  
1.  輸入下列命令以控制 SSO 票證行為：  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  回答問題：  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
     一完成就會收到確認：  
  
     **在此電腦使用 SSO 伺服器。已成功完成此作業。**  
  
## <a name="enabling-the-affiliate-application-xml"></a>啟用分支機構應用程式 XML  
  
#### <a name="to-enable-affiliate-application-xml"></a>若要啟用分支機構應用程式 XML  
  
1.  輸入以下命令：  
  
     `ssomanage -enableapp PeopleSoftApp`  
  
2.  輸入下列命令，列出應用程式並驗證已建立的應用程式：  
  
     `ssoclient.exe –listapps`  
  
     列出可供使用的分支機構應用程式。  
  
     **IBI\YourID-PeopleSoftApp 的應用程式**  
  
3.  輸入下列命令，設定分支機構應用程式認證：  
  
     `ssoclient.exe -setcredentials PeopleSoftApp`  
  
4.  在提示下輸入使用者名稱和密碼。 輸入 PeopleSoftApp 分支機構應用程式的登入認證。  
  
     例如，針對透過 SSO 伺服器進入系統的使用者，輸入使用者識別和密碼。  
  
    -   **使用者識別碼：**`user`  
  
    -   **密碼：**`******`  
  
    -   **確認密碼：**`******`  
  
5.  分支機構應用程式會出現在 PeopleSoft Enterprise 之 BizTalk 配接器的 [傳輸屬性] 對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [使用單一登入](../core/using-single-sign-on2.md)