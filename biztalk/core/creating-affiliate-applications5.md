---
title: "建立 TIBCO EMS 的分支機構應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 191e5b56-dab9-4bf3-9f89-a900907d64e0
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce5df15794886f9177f12f2a9e9a33e3ffdc335f
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="create-affiliate-applications"></a>建立分支機構應用程式
下列步驟說明如何開始使用分支機構應用程式和單一登入 (SSO)。  
  
> [!NOTE]
>  收到 SSO 錯誤時，請確認您設定 BizTalk Server 時有使用網域帳戶，因為企業單一登入服務的功能會受影響。 SSO 僅能在網域帳戶運作  
  
## <a name="create-an-affiliate-application"></a>建立分支機構應用程式  
  
1.  在控制台中開啟**服務**，並確認企業單一登入服務正在執行。  
  
2.  在命令提示中，將目錄變更為 [Enterprise Single Sign-On] 資料夾。  
  
     例如：  
  
     **C:\Program Files\Common Files\Enterprise Single Sign-on >**  
  
3.  使用 [企業單一登入] 命令。 如需命令清單，請使用**-協助**切換。  
  
4.  若要使用 *.XML 為啟動程序來建立分支機構應用程式，請輸入下列命令：  
  
     `ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml`  
  
     其中：  
  
    -   C:\SSOtest 是應用程式 XML 所在的資料夾。  
  
    -   AffiliateApplication.xml 就是您建立的應用程式 XML，其中包含登入資訊。  
  
     例如：  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
        <application name="TIBCO EMS App">  
            <description>TIBCO EMS SSO Application</description>  
            <contact>someone@example.com</contact>  
            <appUserAccount>DomainName\AppUserGroup</appUserAccount>  
            <!—an existing group on the domain controller - >   
            <appAdminAccount>DomainName\AppAdminGroup</appAdminAccount>  
            <!-- an existing account in the domain group - >   
            <field ordinal="0" label="User ID" masked="no" />  
            <field ordinal="1" label="Password" masked="yes" />  
            <flags groupApp="no" allowTickets="yes" enableApp="yes"/>  
        </application>  
    </SSO>  
    ```  
  
 藉由使用範例 XML，分支機構應用程式 TIBCO EMS App 會包含命令提示字元中所顯示的值。  
  
## <a name="create-single-sign-on-tickets"></a>建立單一登入票證  
  
1.  輸入下列命令以控制 SSO 票證行為：  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  回答問題：  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
     一完成就會收到確認：  
  
     **在此電腦使用 SSO 伺服器。已成功完成此作業。**  
  
## <a name="enable-affiliate-application-xml"></a>啟用分支機構應用程式 XML  
  
1.  輸入以下命令：  
  
     `ssomanage -enableapp TIBCO EMSApp`  
  
2.  輸入下列命令，列出應用程式並驗證已建立的應用程式：  
  
     `ssoclient.exe –listapps`  
  
     可供使用的分支機構應用程式隨即以清單形式列出：  
  
     **IBI\YourID-TIBCO EMSApp 的應用程式**  
  
3.  輸入下列命令，設定分支機構應用程式認證：  
  
     `soclient.exe -setcredentials TIBCO EMSApp`  
  
4.  在提示下輸入使用者名稱和密碼。 輸入 TIBCO EMS App 分支機構應用程式的登入認證。  
  
     例如，針對透過 SSO 伺服器進入系統的使用者，輸入使用者識別和密碼。  
  
    -   使用者識別碼：**使用者**  
  
    -   密碼：`******`  
  
    -   確認？ 密碼：`******`  
  
     分支機構應用程式會出現在 BizTalk Adapter for TIBCO EMS**傳輸屬性** 對話方塊。  
  
## <a name="see-also"></a>另請參閱  
[保護配接器](../core/security-in-biztalk-adapter-for-tibco-ems.md)