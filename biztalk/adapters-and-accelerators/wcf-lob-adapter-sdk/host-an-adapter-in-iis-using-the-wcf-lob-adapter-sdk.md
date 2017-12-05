---
title: "裝載於 IIS 使用 WCF LOB Adapter SDK 的配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90b6cd97-01b3-4c98-a190-c6e0ccf24d2b
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 326dc5f3102354c8f2aa6fa785b145b72014f3d3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="host-an-adapter-in-iis-using-the-wcf-lob-adapter-sdk"></a>使用 WCF LOB Adapter SDK 的 IIS 中的配接器主機
本章節包含有關裝載使用所建置的配接器的資訊[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]網際網路資訊服務 (IIS) 中。 如需有關其他裝載選項的詳細資訊，請參閱[裝載服務](https://msdn.microsoft.com/library/ms730158.aspx)。
  
## <a name="use-iis-and-aspnet"></a>使用 IIS 和 ASP.NET
 您可以使用 IIS 來發佈 WCF LOB 配接器 SDK 所建立的配接器啟用 asp.net。 若要裝載所建立的配接器[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，您可以設定網際網路資訊服務 (IIS) 發佈 WCF 服務。 接下來，請考慮如何使用您的 WCF adapterwith ASP.NET。
 
 當裝載在 IIS 中的 WCF 服務，有兩種裝載模式可用：**來並行**和 A**ASP.NET 相容性模式**。 主控模式的預設值是由並行。 與其他 WCF 裝載方案來並行模式行為一致。 因此，在 IIS 中裝載的 WCF 服務的行為與其中一個裝載於主控台應用程式相同。 不過，這可能不是想要因為 web 開發人員可能預期的行為類似於 ASP.NET。 比方說，在由並行模式中，WCF 不會遵守任何中所指定的 URL 為基礎的授權規則`<system.web> <authorization>`web.config 的組態項目。  
  
 ASP.NET 相容性模式可讓 WCF 服務使用的 ASP.NET，所有功能和 ASPX 頁面; 相同的行為不過，您必須採取其他步驟，建立您的 WCF 配接器，以啟用這項功能時。 如需詳細資訊，請參閱： 
 
 [WCF 服務與 ASP.NET](https://msdn.microsoft.com/library/aa702682.aspx)
 
[裝載在 Internet Information Services](https://msdn.microsoft.com/library/ms734710.aspx)

[裝載服務的 WCF](https://msdn.microsoft.com/library/ms730158.aspx)

## <a name="use-the-wcf-adapter-service-development-wizard"></a>使用 WCF 配接器服務開發精靈

使用[!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)]自動建立 Web 專案以裝載您的配接器在網際網路資訊服務 (IIS)。 裝載介面卡然後可供用戶端使用 Windows Communication Framework (WCF) 或 Web 服務。  
  
### <a name="publish-an-adapter-as-a-wcf-service-hosted-in-iis"></a>發佈為 WCF 服務裝載在 IIS 中的配接器  
  
1.  開啟 [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]。 在**檔案**功能表上，選取**新增**，然後選取**網站**。  
  
2.  在**範本**，選取**Visual C#**，然後選取**WCF 配接器服務**。  
  
3.  輸入的資料夾以儲存方案，然後選取**確定**。 **WCF 配接器服務開發精靈**啟動。  
  
4.  在**簡介**頁面上，按一下**下一步**。  
  
5.  在**選擇作業**頁面上，指定要用於這個託管服務繫結、 合約和作業。  
  
    1.  在**選取繫結**清單中，選取配接器繫結來使用，然後按一下**設定**。 這會顯示**設定配接器** 對話方塊。 提供叫用配接器，以及擷取作業的中繼資料所需的值。  
  
    2.  在**安全性**索引標籤上，選取**用戶端認證類型**来傳遞至配接器的用戶端認證時使用。  
  
        |認證類型|Description|  
        |---------------------|-----------------|  
        |**無**|不需要用戶端會出示認證。|  
        |**視窗**|用戶端會使用 Windows 認證。|  
        |**使用者名稱**|用戶端將會提供使用者名稱和密碼。|  
        |**[MSSQLSERVER 的通訊協定內容]**|用戶端將會使用 X.509 憑證驗證。 如果此值設定，請按一下**瀏覽**中**用戶端憑證**區域中，，然後選取要使用的憑證。|  
  
    3.  在**URI 屬性**索引標籤上，指定所需的配接器 URI 參數。 此索引標籤中顯示的項目中公開的屬性視`ConnectionUri Properties`配接器的類別。  
  
    4.  在**繫結屬性**索引標籤上，指定配接器所需的繫結屬性的值。 **一般**> 一節包含一般的設定，例如逾時值。 其他屬性會根據自訂中公開的屬性列出您`AdapterBinding`類別。  
  
6.  一旦您已經指定的設定值，按一下 **連接**。  
  
    1.  從**選取合約型別**清單中，選取要使用的合約。 如此即會填入**選取類別目錄**樹狀控制項的類別和作業可從這張介面卡的清單。 如果配接器實作搜尋功能，透過`MetadataRetrievalClient`類別，您可以輸入中的搜尋詞彙**類別目錄中的搜尋**只有類別和包含搜尋詞彙的作業傳回的欄位。  
  
        > [!NOTE]
        >  只有輸出作業可供選擇。  
  
    2.  從**可用的類別和作業**方塊中，選取要新增，然後再按的項目**新增**。 一旦您加入所需的項目，按一下**下一步**。  
  
7.  在**設定服務與端點行為**頁面上，設定此配接器所需的行為。  
  
    1.  **服務行為組態**章節包含可控制服務之行為項目。 執行精靈之後，您可以藉由編輯 web.config 檔案中修改選取的服務行為。  
  
        |屬性|Description|  
        |--------------|-----------------|  
        |**EnableMetadataExchange**|此值設定為**True**可讓服務用戶端要求的中繼資料發行。 這也可以設定藉由修改\< **serviceMetadata httpGetEnabled =""** \> web.config 中。預設值是**False**|  
        |**IncludeExceptionDetailsinFault**|此值設定為**True**導致 managed 例外狀況資訊傳回 SOAP 錯誤中的用戶端。 這也可以設定藉由修改\< **serviceDebug usingincludeExceptionDetailInFaults =""** \> web.config 中。預設值是**False**。|  
        |**名稱**|服務行為組態名稱。|  
        |**UseServiceCertificate**|這個值會決定服務是否會使用 X.509 憑證來向用戶端處理序。 預設值是**True**。|  
        |**FindValue**|這個值用來搜尋特定的 X.509 憑證的憑證存放區。 也藉由修改設定\< **serviceCredentials findValue =""** \> web.config 中**附註：**指定這個屬性只有當值**UseServiceCertificate**設**True**。|  
        |**StoreLocation**|這個值會指定系統存放區位置來搜尋指定的憑證。 這也可以設定藉由修改\< **serviceCredentials storeLocation =""** \> web.config 中。**注意：**指定的值為這個屬性才**UseServiceCertificate**設**True**。|  
        |**StoreName**|這個值會指定特定的系統存放區，來搜尋指定的憑證。 也藉由修改設定\< **serviceCredentials storeName =""** \> web.config 中**附註：**指定這個屬性只有當值**UseServiceCertificate**設**True**。|  
        |**X509FindType**|搜尋用於 FindValue 的類型稍早指定，以便找出要使用的特定憑證。 也藉由修改設定\< **serviceCredentials x509FindType =""** \> web.config 中**附註：**指定這個屬性只有當值**UseServiceCertificate**設**True**。|  
  
    2.  **端點行為組態**區段控制端點行為。  
  
        |屬性|Description|  
        |--------------|-----------------|  
        |**名稱**|端點行為的名稱|  
        |**AuthenticationType**|這個值會指示配接器來取得用戶端認證的內送文件的位置。 若要啟用用戶端指定要向服務驗證的用戶端憑證，將此設**ClientCredentialUsernamePassword**。 若要啟用用戶端指定的使用者名稱和密碼做為 HTTP 標頭的一部分，將此設**HTTPUsernamePassword**。 若要啟用用戶端指定認證，透過 ClientCredential 介面，將此設**自動**。如果失敗，用戶端才能將認證傳遞做為 HTTP 標頭的一部分。<br /><br /> 這個值也可以藉由修改設定\< **[endpointbehavior] adapterSecurityBridgeType** \> web.config 中。預設值是**自動**。|  
        |**UsernameHeader**|這會指定將用來傳遞至服務的使用者名稱標頭名稱。 HTTP 標頭的詳細資訊，請參閱 < 自訂 HTTP 和 SOAP 標頭的支援 >，網址[http://go.microsoft.com/fwlink/?LinkId=106692](http://go.microsoft.com/fwlink/?LinkId=106692)<br /><br /> 這個值也可以藉由修改設定\< **[endpointbehavior] usernameHttpHeader** \> web.config 中。**注意：**您必須指定此屬性的值，如果**AuthenticationType**設**HTTPUserNamePassword**。  如果設定為**自動**，這是選擇性屬性。|  
        |**PasswordHeader**|這會指定將用來將使用者密碼傳遞給服務的標頭名稱。 HTTP 標頭的詳細資訊，請參閱 < 支援的自訂 HTTP 和 SOAP 標頭 >，網址[http://go.microsoft.com/fwlink/?LinkId=106692](http://go.microsoft.com/fwlink/?LinkId=106692)<br /><br /> 這個值也可以藉由修改設定 <**[endpointbehavior] passwordHttpHeader**< web.config 中。**注意：**您必須指定此屬性的值，如果**AuthenticationType**設**HTTPUserNamePassword**。 如果設定為**自動**，這是選擇性屬性。|  
  
    3.  設定所要的行為後, 按一下**下一步**才能繼續。  
  
8.  在**設定服務端點繫結和位址** 頁面上，您可以設定做為合約的位址和繫結屬性。 選取在合約**選取要設定的合約**清單，，然後輸入所需的值在**設定的位址和合約繫結** 對話方塊。  
  
    1.  選取**BindingConfiguration**下繫結屬性的項目。 此精靈只支援基本 HTTP 繫結，讓繫結組態 欄位會自動設為**System.ServiceModel.Configuration.BasicHttpBindingElement**。 若要變更此繫結的組態屬性，按一下省略符號**...** 按鈕，可選取色彩。 若要使用安全通訊通道，您都必須設定**模式**屬性**傳輸**。 這是預設值。  
  
    2.  選取**EndpointName**，然後輸入所需的端點名稱。  
  
    3.  若要套用您的變更，請按一下**套用**。  
  
9. 若要繼續進行，請按 **[下一步]**。 [摘要] 頁面會列出所選取的配接器作業的樹狀結構。  
  
10. 檢閱 [摘要]，然後按一下**完成**。  
  
11. 精靈會建立 Web 專案，並將下列檔案。  
  
    |檔案|Description|  
    |----------|-----------------|  
    |.svc|服務參考到 WCF proxy 的檔案。|  
    |.cs|實作 WCF proxy。|  
    |web.config|包含\<**端點**\, \<**繫結**\>，和\<**行為**\>元素\<**系統。ServiceModel**\>|  
  
12. 發佈 WCF 服務專案。  
  
    1.  以滑鼠右鍵按一下方案總管 中的專案，然後按一下**發行**。  
  
    2.  在**發行網站**對話方塊方塊中，指定 WCF 服務的目標 URL。  
  
    3.  選取**允許更新此先行編譯的網站**。  
  
    4.  選取**使用固定命名和單一網頁組件**。  
  
    5.  選取**啟用強式命名的先行編譯的組件**，然後指定要使用的簽章金鑰。  
  
13. 若要發行的網站，按一下 **確定**。  
  
14. 請確認服務已成功發行。  
  
    1.  啟動 IIS 管理主控台。  按一下**啟動**，指向 **系統管理工具**，然後按一下  **Internet Information Services**。  
  
    2.  瀏覽至您用來發行服務的節點。  如果服務已發行為 http://localhost/myservice，瀏覽至**Internet Information Services**> **電腦名稱**> **網站** >  **Default Web Site**> **myservice**。  
  
    3.  在右窗格中，.svc 檔案中，以滑鼠右鍵按一下，然後按一下 **瀏覽**。 Web 網頁會顯示與服務的相關資訊。 您現在可以使用從用戶端應用程式的 WCF 或 Web 服務呼叫，以使用此服務。 

## <a name="security"></a>安全性
當配接器裝載於服務中時，從用戶端應用程式的呼叫會使用配接器安全性橋接器將用戶端認證傳遞給配接器。  
  
 當 WCF 用戶端會傳送至 WCF 服務驗證時，服務通常會使用驗證。 不過，在配接器的情況下的觀念並擷取基礎 LOB 系統搭配使用的驗證資訊。 這被實作透過配接器安全性橋接器，會呈現為端點行為。 身為配接器開發人員，沒有任何需要實作，以充分利用這項功能。不過，在部署配接器時，您必須考慮如何在用戶端將提供認證給服務。  
  
 如果您使用訊息層級安全性，配接器安全性橋接器可以擷取任何繫結上的用戶端應用程式所傳送的 ClientCredentials。 如果您使用基本 HTTP 繫結，您可以改為選取要用於自訂的標頭傳遞使用者名稱和密碼資訊。 建議使用 WCF 提供的 ClientCredential 類別傳遞認證，但是許多 Web 服務用戶端應用程式必須將認證傳遞使用的自訂標頭。  
  
 以下是範例設定配接器從中尋找用戶端應用程式提供 ClientCredentials 中的認證。 如果找不到，配接器接著會查看所指定的 HTTP 要求標頭。  
  
```  
<endpointBehaviors>  
   <behavior name="customEndpointBehavior">  
      <endpointBehavior usernameHttpHeader="UNHdr" passwordHttpHeader="PWHdr"  
         adapterSecurityBridgeType="Auto" />  
    </behavior>  
</endpointBehaviors>  
```      
  
## <a name="see-also"></a>請參閱  
 [開發活動](../../esb-toolkit/development-activities.md)