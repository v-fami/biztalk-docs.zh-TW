---
title: 如何動態設定已使用的 Web 服務的 URI |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 95829a28-7898-4757-87cc-40fc99bf707e
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a33f8d7c82130e3e0867d51a1575f40ac4442b7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998519"
---
# <a name="how-to-dynamically-set-the-uri-of-a-consumed-web-service"></a>如何動態設定已使用之 Web 服務的 URI
為已使用的 Web 服務建立 Web 連接埠時，可以選取動態連接埠繫結。 選取動態連接埠繫結時，您必須在執行階段設定已使用之 Web 服務的 URI。 已選取的 URI 所呼叫的 Web 服務，必須和您用來建立 Web 連接埠類型的 Web 服務具備相同的 Web Proxy。  
  
> [!NOTE]
>  本主題說明如何以程式設計的方式，在協調流程中設定動態 SOAP 傳送埠屬性。 然而，不管傳送埠是靜態還是動態的，您都可以在協調流程或自訂的管線元件中設定這些屬性。 如需有關自訂管線元件的詳細資訊，請參閱 <<c0> [ 開發自訂管線元件](../core/developing-custom-pipeline-components.md)。  
  
 Web 連接埠的動態連接埠繫結與非 Web 連接埠的動態連接埠繫結，具有不同的行為。 選取非 Web 連接埠的動態繫結時，無法使用 SOAP 配接器。  
  
 以動態 Web 連接埠使用 Web 服務時，傳送埠屬性會設定為預設值。 其中有些值會在內部設定和其他值則預設為中所設定的值**SOAP 配接器處理常式**屬性頁。 使用動態傳送埠時，您可以覆寫協調流程中的這些值。 如需詳細資訊，請參閱 <<c0> [ 考量當 Consuming Web Services](../core/considerations-when-consuming-web-services.md)。  
  
## <a name="dynamically-change-the-uri-of-a-consumed-web-service"></a>動態變更已使用的 Web 服務的 URI  
  
1.  新增 Web 連接埠中所述[如何新增 Web 連接埠](../core/how-to-add-a-web-port.md)。 不過，而不是選取**指定現在**連接埠繫結，選取**動態**連接埠繫結，如下圖所示。  
  
     ![](../core/media/ebiz-prog-wsc-dynamic.gif "ebiz_prog_wsc_dynamic")  
  
2.  在 協調流程呼叫所使用的 Web 服務中，新增**運算式**在之前的某個時間點的圖形**傳送**您已經連接到 Web 連接埠的圖形。  
  
3.  在 **運算式**圖形中新增運算式，類似於：  
  
    ```  
    myWebPort(Microsoft.XLANGs.BaseTypes.Address) = "http://orders/myCompany.asmx";  
    ```  
  
> [!NOTE]
>  您可從不同位置 (包含內送訊息、SQL 資料庫或企業營運系統應用程式)，擷取 [BizTalk 運算式編輯器] 中所使用的 URI。  
  
## <a name="dynamically-modify-send-port-properties"></a>動態修改傳送埠屬性  
  
1. 在 **建構的訊息**圖形，您用來建構 Web 訊息，新增**訊息指派**圖形如果尚未存在。  
  
2. 在 **訊息指派**圖形中新增運算式，類似於：  
  
   ```  
   myWebMessage(SOAP.UseSSO) = true;  
   ```  
  
   SOAP 傳送埠的所有屬性都是使用 SOAP 命名空間。  
  
   下表列出使用動態 Web 連接埠時您可以設定的 SOAP 傳送埠屬性。  
  
|        屬性名稱         |  類型   |                                                                                                                                                                                                                                                                                                 描述                                                                                                                                                                                                                                                                                                  |
|------------------------------|---------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **AuthenticationScheme**   | String  |                                                                                                                                                                                                                             呼叫 Web 服務所使用的驗證方法<br /><br /> 預設值： 匿名<br /><br /> 其他允許的值： 基本、 摘要式、 NTLM                                                                                                                                                                                                                              |
|         **使用者名稱**         | String  |                                                                                                                                                                                                                                                         指定要用於存取目標 Web 服務的使用者名稱。<br /><br /> 預設值： 空白                                                                                                                                                                                                                                                          |
|         **密碼**         | String  |                                                                                                                                                                                                                                                          要提供給伺服器驗證的使用者密碼。<br /><br /> 預設值： 空白                                                                                                                                                                                                                                                           |
|    **ClientCertificate**     | String  |                                                                                                                                                                                                                                                        用戶端安全通訊端層 (SSL) 憑證的指紋。<br /><br /> 預設值： 空白                                                                                                                                                                                                                                                         |
|          **UseSSO**          | 布林 |                                                                                                                                                                                                                                                       指示此 Web 連接埠是否使用「單一登入」(SSO)。<br /><br /> 預設值：False                                                                                                                                                                                                                                                        |
| **AffiliateApplicationName** | String  |                                                                                                                                                                                                                                  此 Web 連接埠將用於贖回用戶端認證票證的 SSO 應用程式名稱。<br /><br /> 預設值： 空白                                                                                                                                                                                                                                   |
|    **UseHandlerSetting**     | 布林 |                                                                                                                                                                                      指示此 Web 連接埠是否使用 SOAP 傳送處理常式的 HTTP Proxy 設定。 **注意︰** 如果**UseProxy**設定的內容屬性，然後**UseHandlerSetting**內容屬性會被忽略。 <br /><br /> 預設值：False                                                                                                                                                                                       |
|         **UseProxy**         | 布林 |                                                                                                                                                                                 指示此 Web 連接埠是否使用 Proxy 伺服器來存取目標 Web 服務。 **注意︰** 如果**UseProxy**設定的內容屬性，然後**UseHandlerSetting**內容屬性會被忽略。 <br /><br /> 預設值：False                                                                                                                                                                                  |
|       **ProxyAddress**       | String  |                                                                                                                                                                                                                                      用於 Web 服務呼叫的 HTTP Proxy 位址。<br /><br /> 預設值： 從 SOAP 傳送處理常式屬性擷取。                                                                                                                                                                                                                                      |
|        **ProxyPort**         | Integer |                                                                                                                                                                                                                                       用於 Web 服務呼叫的 HTTP Proxy 連接埠。<br /><br /> 預設值： 從 SOAP 傳送處理常式屬性擷取。                                                                                                                                                                                                                                        |
|      **ProxyUsername**       | String  |                                                                                                                                                                                                                                                 用於 HTTP Proxy 的使用者名稱。<br /><br /> 預設值： 從 SOAP 傳送處理常式屬性擷取。                                                                                                                                                                                                                                                 |
|      **ProxyPassword**       | String  |                                                                                                                                                                                                                                                 用於 HTTP Proxy 的密碼。<br /><br /> 預設值： 從 SOAP 傳送處理常式屬性擷取。                                                                                                                                                                                                                                                  |
| **ClientConnectionTimeout**  |  Int32  |                                                                                                                                                                                                                                           HTTP 用戶端連線逾時值。<br /><br /> 預設值： 相同預設 ASP.NET HTTP 連線逾時。                                                                                                                                                                                                                                            |
|         **類型名稱**         | String  |                                                                                                                                                                                                                                                  指定包含要叫用的 Web 方法的類別名稱。<br /><br /> 預設值： 空白                                                                                                                                                                                                                                                  |
|        **MethodName**        | String  | 指定將要叫用之類別的方法。 **注意：** 來設定**MethodName**屬性的靜態 SOAP 傳送埠以程式設計方式，您需要設定**方法名稱**而 **[稍後指定]** 中**Web 服務**索引標籤**SOAP 傳輸屬性**在 BizTalk Server 管理主控台中的對話方塊。 如需詳細資訊**SOAP 傳輸屬性** 對話方塊中，請參閱**SOAP 傳輸屬性對話方塊、 Web 服務**索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。 <br /><br /> 預設值： 空白 |
|       **組件名稱**       | String  |                                                                                                                                                                                                                                                      識別要載入和執行的 .NET 類型與組件。<br /><br /> 預設值： 空白                                                                                                                                                                                                                                                       |
|      **UnknownHeaders**      | String  |                                                                                                                                                                                                                                                           指定未知 SOAP 標頭的序列化清單。<br /><br /> 預設值： 空白                                                                                                                                                                                                                                                            |
|       **UserDefined**        | String  |                                                                                                                                                                                                                                                                        定義使用者定義的類別<br /><br /> 預設值： 空白                                                                                                                                                                                                                                                                         |
|        **UseSoap12**         | 布林 |                                                                                                                                                                                                             指定產生支援 SOAP 1.2 通訊協定的 Proxy 程式碼。 若此屬性為 False，則會產生 SOAP 1.1 相容的 Proxy 程式碼。<br /><br /> 預設值：False                                                                                                                                                                                                             |
  
> [!NOTE]
>  除了**ClientConnectionTimeout**設定，這些值只能以動態方式設定時使用**動態**連接埠繫結。 它們是唯讀狀態時使用**立即指定**連接埠繫結。 您可以設定**ClientConnectionTimeout**設定**現在指定**並**動態**連接埠繫結。  
  
## <a name="see-also"></a>另請參閱  
 [SOAP 標頭與已使用的 Web 服務](../core/soap-headers-with-consumed-web-services.md)   
 [建立 Web 連接埠](../core/creating-web-ports.md)