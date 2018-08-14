---
title: 裝載配接器使用 WCF LOB 配接器 SDK 在 IIS 中的 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 90b6cd97-01b3-4c98-a190-c6e0ccf24d2b
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 570c844b7e41c8fd4deb340e6a0ce1bf598ae24b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976135"
---
# <a name="host-an-adapter-in-iis-using-the-wcf-lob-adapter-sdk"></a>主機使用 WCF LOB 配接器 SDK 在 IIS 中的配接器
本章節包含有關裝載使用所建置的配接器的資訊[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]在網際網路資訊服務 (IIS)。 如需其他裝載選項的詳細資訊，請參閱[裝載的服務](https://msdn.microsoft.com/library/ms730158.aspx)。

## <a name="use-iis-and-aspnet"></a>使用 IIS 和 ASP.NET
 您可以使用 IIS 來發佈 WCF LOB 配接器 sdk 所建立的配接器啟用 asp.net。 若要裝載所建立的配接器[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，您可以設定 Internet Information Services (IIS) 發佈 WCF 服務。 接下來，請考慮如何使用您的 WCF adapterwith ASP.NET。

 當裝載在 IIS 中的 WCF 服務，有兩種的裝載模式可用：**並排顯示**和 A**ASP.NET 相容性模式**。 裝載模式的預設值為並排顯示。 並排顯示模式的行為一致的方式與其他 WCF 裝載解決方案。 因此，在 IIS 中裝載的 WCF 服務的行為與其中一個裝載於主控台應用程式相同。 不過，這可能不想因為 web 開發人員可能預期的行為類似於 ASP.NET。 比方說，在並排顯示模式中，WCF 不會遵守任何在指定的 URL 為基礎的授權規則`<system.web> <authorization>`web.config 的組態項目。  

 ASP.NET 相容性模式可讓 WCF 服務使用的 ASP.NET 中，所有功能，並與 ASPX 頁面; 相同的行為不過，您必須採取其他步驟，建立您的 WCF 配接器，以啟用此功能時。 如需詳細資訊，請參閱： 

 [WCF 服務與 ASP.NET](https://msdn.microsoft.com/library/aa702682.aspx)

[在 Internet Information Services 中裝載](https://msdn.microsoft.com/library/ms734710.aspx)

[裝載服務的 WCF](https://msdn.microsoft.com/library/ms730158.aspx)

## <a name="use-the-wcf-adapter-service-development-wizard"></a>使用 WCF 配接器服務開發精靈

使用[!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)]自動建立 Web 專案來裝載您的配接器在網際網路資訊服務 (IIS)。 裝載配接器則可供用戶端使用 Windows Communication Framework (WCF) 或 Web 服務。  

### <a name="publish-an-adapter-as-a-wcf-service-hosted-in-iis"></a>發佈為 WCF 服務裝載在 IIS 中的配接器  

1. 開啟 [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)] 在上**檔案**功能表上，選取**新增**，然後選取**網站**。  

2. 在 **範本**，選取**Visual C#**，然後選取**WCF 配接器服務**。  

3. 輸入的資料夾來儲存方案，然後選取**確定**。 **WCF 配接器服務開發精靈**啟動。  

4. 在 [**簡介**頁面上，按一下**下一步]**。  

5. 在 **選擇作業**頁面上，指定要用於這個託管服務繫結、 合約和作業。  

   1.  在 **選取的繫結**清單中，選取配接器繫結，以使用此項目，然後按一下**設定**。 這會顯示**設定配接器** 對話方塊。 提供叫用配接器，以及擷取作業的中繼資料所需的值。  

   2.  在 **安全性**索引標籤上，選取**用戶端認證類型**時將用戶端認證傳遞至配接器使用。  

       |認證類型|描述|  
       |---------------------|-----------------|  
       |**無**|用戶端不需要出示認證。|  
       |**視窗**|用戶端會使用 Windows 認證。|  
       |**使用者名稱**|用戶端會提供使用者名稱和密碼。|  
       |**[MSSQLSERVER 的通訊協定內容]**|用戶端會使用 X.509 憑證進行驗證。 如果此值設定，請按一下**瀏覽**中**用戶端憑證**區域，然後選取要使用的憑證。|  

   3.  在  **URI 屬性**索引標籤上，指定所需的配接器 URI 參數。 此索引標籤中顯示的項目而異中公開的屬性`ConnectionUri Properties`配接器的類別。  

   4.  在 **繫結屬性**索引標籤上，指定所需的配接器的繫結屬性的值。 **一般**區段包含常見的設定，例如逾時值。 其他屬性會列出根據中公開的自訂屬性您`AdapterBinding`類別。  

6. 一旦您指定的設定值，按一下**Connect**。  

   1.  從**選取合約的型別**清單中，選取要使用的合約。 這會填入**選取一個類別**樹狀控制項的類別和作業可從這張介面卡清單。 如果配接器實作搜尋功能，透過`MetadataRetrievalClient`類別，您可以輸入中的搜尋詞彙**類別目錄中的搜尋**只有 「 類別 」 和 「 包含搜尋詞彙的作業傳回的欄位。  

       > [!NOTE]
       >  只有輸出的作業可供選擇。  

   2.  從**可用的類別和作業**方塊中，選取的項目來新增，然後按一下**新增**。 一旦您加入所需的項目，按一下**下一步**。  

7. 在 **設定服務與端點行為**頁面上，設定此配接器所需的行為。  

   1.  **服務行為組態**區段包含可控制服務之行為的項目。 執行精靈之後，您可以藉由編輯 web.config 檔案來修改所選取的服務行為。  

       |屬性|描述|  
       |--------------|-----------------|  
       |**EnableMetadataExchange**|此值設定為 **，則為 True**可讓服務用戶端要求的中繼資料發行。 這也可以設定藉由修改\< **serviceMetadata httpGetEnabled =""** \> web.config 中。預設值是**False**|  
       |**IncludeExceptionDetailsinFault**|此值設定為 **，則為 True**導致 managed 例外狀況資訊傳回 SOAP 錯誤中的用戶端。 這也可以設定藉由修改\< **serviceDebug usingincludeExceptionDetailInFaults =""** \> web.config 中。預設值是**False**。|  
       |**名稱**|服務行為組態名稱。|  
       |**UseServiceCertificate**|這個值會決定服務是否會使用 X.509 憑證來向用戶端處理序。 預設值是 **，則為 True**。|  
       |**FindValue**|這個值用來搜尋特定的 X.509 憑證的憑證存放區。 這也可以設定藉由修改\< **serviceCredentials findValue =""** \> web.config 中**附註：** 指定此屬性才的值**UseServiceCertificate**設定為 **，則為 True**。|  
       |**StoreLocation**|這個值會指定要搜尋指定的憑證的系統存放區位置。 這也可以設定藉由修改\< **serviceCredentials storeLocation =""** \> web.config 中。**注意：** 指定的值為這個屬性只有當**UseServiceCertificate**設定為 **，則為 True**。|  
       |**StoreName**|這個值會指定特定的系統存放區，來搜尋指定的憑證。 這也可以設定藉由修改\< **serviceCredentials storeName =""** \> web.config 中**附註：** 指定此屬性才的值**UseServiceCertificate**設定為 **，則為 True**。|  
       |**X509FindType**|要使用 FindValue 的搜尋類型稍早指定以找出要使用的特定憑證。 這也可以設定藉由修改\< **serviceCredentials x509FindType =""** \> web.config 中**附註：** 指定此屬性才的值**UseServiceCertificate**設定為 **，則為 True**。|  

   2.  **端點行為組態**區段會控制端點行為。  

       |屬性|描述|  
       |--------------|-----------------|  
       |**名稱**|端點行為的名稱|  
       |**AuthenticationType**|此值會指示此配接器如何取得用戶端的內送文件的認證。 若要啟用用戶端指定用戶端憑證來向服務驗證，將此設**ClientCredentialUsernamePassword**。 若要啟用用戶端指定的使用者名稱和密碼做為 HTTP 標頭的一部分，將此設**HTTPUsernamePassword**。 若要啟用用戶端指定認證，透過 ClientCredential 介面，將此設**自動**。如果失敗，用戶端可以將認證傳遞做為 HTTP 標頭的一部分。<br /><br /> 此值也可以設定藉由修改\< **[endpointbehavior] adapterSecurityBridgeType** \> web.config 中。預設值是**自動**。|  
       |**UsernameHeader**|這會指定將用來傳遞至服務的使用者名稱標頭的名稱。 HTTP 標頭的詳細資訊，請參閱 < 自訂 HTTP 與 SOAP 標頭支援 > 網址 [http://go.microsoft.com/fwlink/?LinkId=106692](http://go.microsoft.com/fwlink/?LinkId=106692)<br /><br /> 此值也可以設定藉由修改\< **[endpointbehavior] usernameHttpHeader** \> web.config 中。**注意︰** 您必須指定此屬性的值，如果**AuthenticationType**設定為**HTTPUserNamePassword**。  如果設定為**自動**，這是選擇性屬性。|  
       |**PasswordHeader**|這會指定將用來將使用者密碼傳遞至服務的標頭的名稱。 如需有關 HTTP 標頭的詳細資訊，請查看 [支援的自訂 HTTP 和 SOAP 標頭] [http://go.microsoft.com/fwlink/?LinkId=106692](http://go.microsoft.com/fwlink/?LinkId=106692)<br /><br /> 此值也可以藉由修改設定 <**[endpointbehavior] passwordHttpHeader**< web.config 中。**注意︰** 您必須指定此屬性的值，如果**AuthenticationType**設定為**HTTPUserNamePassword**。 如果設定為**自動**，這是選擇性屬性。|  

   3.  設定之後所要的行為，請按一下**下一步**以繼續。  

8. 在 [**設定的服務端點繫結和位址**] 頁面上，您可以設定的位址和繫結的屬性，做為合約。 選取合約**選取要設定的合約**清單，然後再輸入所需的值，在**設定的位址和合約繫結** 對話方塊。  

   1.  選取  **BindingConfiguration**下繫結屬性的項目。 此精靈只支援基本 HTTP 繫結，讓繫結組態 欄位會自動設為**System.ServiceModel.Configuration.BasicHttpBindingElement**。 若要變更此繫結的組態屬性，按一下省略符號 **...** 按鈕，可選取色彩。 若要使用的安全通訊通道，您都必須設定**模式**屬性設**傳輸**。 這是預設值。  

   2.  選取  **EndpointName**，然後輸入所需端點的名稱。  

   3.  若要套用您的變更，請按一下**套用**。  

9. 若要繼續進行，請按 **[下一步]**。 [摘要] 頁面會列出所選取的配接器作業的樹狀結構。  

10. 檢閱 [摘要]，然後按**完成**。  

11. 此精靈建立 Web 專案，並將下列檔案。  


    |    檔案    |                                                描述                                                 |
    |------------|------------------------------------------------------------------------------------------------------------|
    |    .svc    |                               參考至 WCF proxy 的服務檔案。                               |
    |    .cs     |                                         實作 WCF proxy。                                          |
    | web.config | 包含\<**端點**\, \<**繫結**\>，以及\<**行為**\>項目\<**系統。ServiceModel**\> |


12. 發佈 WCF 服務專案。  

    1.  以滑鼠右鍵按一下方案總管 中的專案，然後按一下**發佈**。  

    2.  在 **發行網站**對話方塊方塊中，指定 WCF 服務的目標 URL。  

    3.  選取 **讓這個先行編譯的站台更新**。  

    4.  選取 **使用固定命名和單一頁面的組件**。  

    5.  選取 **啟用強式命名上先行編譯的組件**，然後指定要使用的簽署金鑰。  

13. 若要發佈的網站，請按一下**確定**。  

14. 請確認已成功發行服務。  

    1.  啟動 IIS 管理主控台。  按一下 **開始**，指向**系統管理工具**，然後按一下**Internet Information Services**。  

    2.  瀏覽至您用來發行服務的節點。  如果服務已為發行 http://localhost/myservice ， 瀏覽至**Internet Information Services**> **電腦名稱**> **網站**>  **Default Web Site**> **myservice**。  

    3.  在右窗格中，請在.svc 檔案中，以滑鼠右鍵按一下，，然後按一下**瀏覽**。 網頁會顯示與服務的相關資訊。 您現在可以使用從用戶端應用程式的 WCF 或 Web 服務呼叫，以使用這項服務。 

## <a name="security"></a>Security
當配接器裝載於服務中時，從用戶端應用程式的呼叫會使用配接器安全性橋接器將用戶端認證傳遞給配接器。  

 當 WCF 用戶端會將驗證傳送至 WCF 服務時，通常服務會使用驗證。 不過，在配接器的情況下其概念是擷取基礎 LOB 系統搭配使用的驗證資訊。 這是透過配接器安全性橋接器，會呈現為端點行為來實作。 身為配接器開發人員，並不需要實作，以善用這項功能;不過，在部署配接器時，您必須考慮如何在用戶端還會提供認證給服務。  

 如果您使用訊息層級安全性，配接器安全性橋接器可以擷取 ClientCredentials 傳送的任何繫結上的用戶端應用程式。 如果您使用的基本 HTTP 繫結，您可以改為選擇使用自訂標頭傳遞的使用者名稱和密碼資訊。 建議使用 WCF 提供的 ClientCredential 類別傳遞認證，不過許多 Web 服務用戶端應用程式必須使用自訂標頭，將認證傳遞。  

 以下是範例組態，配接器尋找認證在用戶端應用程式提供 ClientCredentials 中的位置。 如果找不到，配接器接著會尋找在指定的 HTTP 要求標頭中。  

```  
<endpointBehaviors>  
   <behavior name="customEndpointBehavior">  
      <endpointBehavior usernameHttpHeader="UNHdr" passwordHttpHeader="PWHdr"  
         adapterSecurityBridgeType="Auto" />  
    </behavior>  
</endpointBehaviors>  
```      

## <a name="see-also"></a>另請參閱  
 [開發活動](../../esb-toolkit/development-activities.md)