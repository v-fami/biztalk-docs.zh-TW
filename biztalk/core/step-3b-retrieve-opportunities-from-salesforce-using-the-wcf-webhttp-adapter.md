---
title: 步驟 3b： 擷取商機的詳細資料來自使用 Wcf-webhttp 配接器的 Salesforce |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 115c908f-777b-4c51-85ea-71d639b01775
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05312890d7cd21810651e7e41a8418080912f72f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279550"
---
# <a name="step-3b-retrieve-opportunity-details-from-salesforce-using-the-wcf-webhttp-adapter"></a>步驟 3b： 擷取來自 Salesforce 使用 Wcf-webhttp 配接器的機會詳細資料
在本節中，我們會著重於處理內送商機通知的協調流程、從通知擷取商機名稱，並用來建立要求查詢以傳送至 Salesforce。 這樣會擷取與商機關聯的產品相關特定詳細資料。 來自 Salesforce 的查詢回應會由 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收。 若要達到此目標，我們會執行下列步驟：  
  
-   建立結構描述和訊息變數以傳送查詢訊息至 Salesforce。  
  
-   建立對應以使用商機通知中的值來建立查詢以擷取與該商機相關聯的產品詳細資料。  
  
-   建立結構描述以接收來自 Salesforce 的查詢回應。  
  
-   為要求和回應結構描述建立訊息變數。  
  
## <a name="create-schema-and-message-variables-to-send-query-messages-to-salesforce"></a>建立結構描述和訊息變數，以傳送查詢訊息至 Salesforce  
 若要擷取來自 Salesforce 的產品詳細資料，使用可透過商機通知的資訊，我們需要傳送查詢到 Salesforce。 查詢會以 XML 訊息傳送至 Salesforce。 因此，在下列程序建立要求訊息的結構描述。 在後續的程序，我們會將對應的商機通知的結構描述與此結構描述來建構查詢來擷取產品詳細資料的機會。  
  
#### <a name="to-create-a-schema-for-sending-query-request"></a>若要建立查詢要求傳送的結構描述  
  
1.  加入新的結構描述[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案。 將它命名為 `QueryRequest.xsd`。  
  
2.  重新命名的根節點`QueryRequest`。 新增 QueryRequest 記錄下的子欄位項目並將其命名`Query`。  
  
3.  升級**查詢**，使其可供協調流程中使用的結構描述中的項目。 在接下來的步驟中，我們將使用此升級的項目來將查詢字串指定。  
  
     以滑鼠右鍵按一下**查詢**項目，指向**升階**，然後按一下 **快速升級**。 這會導致建立**PropertySchema.xsd**結構描述與**查詢**項目。 請注意命名空間，如 PropertySchema。 您必須在未來此步驟時設定中的實體連接埠[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
4.  儲存所有變更。  
  
## <a name="map-the-opportunity-notification-schema-to-the-query-schema"></a>將有機會通知結構描述對應至查詢的結構描述  
 若要擷取與該商機相關聯的產品詳細資料，我們需要與下列類似的查詢傳送至 Salesforce:  
  
```  
SELECT Amount, Id, Name,(SELECT Quantity, ListPrice, PricebookEntry.UnitPrice, PricebookEntry.Name FROM OpportunityLineItems) FROM Opportunity Where Name = '<opportunity_name>'  
```  
  
 在上一個程序中我們已經建立查詢訊息的結構描述。 在此程序中，我們商機通知結構描述對應至查詢要求結構描述，並使用運算質來建構這個查詢。 此查詢會當做值傳遞給**查詢**中的項目**QueryRequest.xsd**結構描述。  
  
#### <a name="to-map-the-opportunity-notification"></a>若要將對應商機通知  
  
1.  新增對應到[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案。 Map 命名`Notification_QueryRequest.btm`。  
  
2.  將來源結構描述設**NotificationService_soap_sforce_com_2005_09_outbound.xsd**。 將目的結構描述設**QueryRequest**.xsd。  
  
3.  新增**字串串連**運算質至對應的介面。 開啟**設定字串串連運算質**對話方塊指定的輸入的值，如下所示：  
  
    |||  
    |-|-|  
    |Input [0]|選取量、 識別碼、 名稱 (選取 Quantity、 ListPrice PricebookEntry.UnitPrice，PricebookEntry.Name 從 OpportunityLineItems) 從有機會 Where Name = '|  
    |Input [1]|若要使用名稱元素的值做為第二個輸入的運算質連接來源結構描述中的名稱項目。|  
    |輸入 [2]|'**附註：** 最後一個的輸入值，指定只右單引號 （'）。|  
  
     下列螢幕擷取畫面說明的組態**字串串連**運算質。  
  
     ![設定字串串連運算質](../core/media/bts-sf-stringconcatenate.jpg "BTS_SF_StringConcatenate")  
  
     當串連三個輸入的參數時，它將會形成所需的查詢傳送至 Salesforce。  
  
4.  連接字串串連運算質至目的結構描述中的查詢項目，如下列螢幕擷取畫面所示。  
  
     ![對應至查詢的結構描述的通知回應](../core/media/bts-sf-notification-query-mapping.jpg "BTS_SF_Notification_Query_Mapping")  
  
5.  將變更儲存到對應。  
  
## <a name="creating-schema-to-receive-the-query-response-message"></a>建立用來接收查詢回應訊息的結構描述  
 在本節中，我們會建立要接收來自 Salesforce 的查詢回應訊息的結構描述。 在本節中，我們可以手動建立查詢回應結構的描述。  
  
#### <a name="to-create-a-schema-to-receive-the-query-response"></a>若要建立接收查詢回應結構描述  
  
1.  加入新的結構描述[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案，並命名`QueryResult.xsd`。  
  
2.  Salesforce [QueryResult](http://go.microsoft.com/fwlink/?LinkId=287017)物件描述接收來自 Salesforce 的查詢回應。 因此，我們會建置結構描述來描述下列：  
  
    ```  
    <?xml version="1.0" encoding="utf-16" ?>  
    - <xs:schema xmlns="http://BtsSalesforceIntegration.QueryResult" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" targetNamespace="http://BtsSalesforceIntegration.QueryResult" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
      - <xs:element name="QueryResult">  
        - <xs:complexType>  
          - <xs:sequence>  
            <xs:element name="done" type="xs:string" />  
            - <xs:sequence>  
              - <xs:element name="records">  
                - <xs:complexType>  
                  - <xs:sequence>  
                    <xs:element name="Id" type="xs:string" />  
                    <xs:element name="Amount" type="xs:string" />  
                    <xs:element name="Name" type="xs:string" />  
                    - <xs:sequence>  
                      - <xs:element name="OpportunityLineItems">  
                        - <xs:complexType>  
                          - <xs:sequence>  
                            <xs:element name="done" type="xs:string" />  
                            - <xs:sequence minOccurs="1" maxOccurs="unbounded">  
                              - <xs:element name="records">  
                                - <xs:complexType>  
                                  - <xs:sequence>  
                                    <xs:element name="Quantity" type="xs:string" />  
                                    <xs:element name="ListPrice" type="xs:string" />  
                                    - <xs:element name="PricebookEntry">  
                                      - <xs:complexType>  
                                        - <xs:sequence>  
                                          <xs:element name="UnitPrice" type="xs:string" />  
                                          <xs:element name="Name" type="xs:string" />  
                                        </xs:sequence>  
                                        <xs:attribute name="type" type="xs:string" />  
                                        <xs:attribute name="url" type="xs:string" />  
                                      </xs:complexType>  
                                    </xs:element>  
                                  </xs:sequence>  
                                  <xs:attribute name="type" type="xs:string" />  
                                  <xs:attribute name="url" type="xs:string" />  
                                </xs:complexType>  
                              </xs:element>  
                            </xs:sequence>  
                            <xs:element name="totalSize" type="xs:string" />  
                          </xs:sequence>  
                        </xs:complexType>  
                      </xs:element>  
                    </xs:sequence>  
                  </xs:sequence>  
                  <xs:attribute name="type" type="xs:string" />  
                  <xs:attribute name="url" type="xs:string" />  
                </xs:complexType>  
              </xs:element>  
            </xs:sequence>  
            <xs:element name="totalSize" type="xs:string" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:schema>  
    ```  
  
     結構描述結構看起來應該如下所示：  
  
     ![來自 Salesforce 的查詢回應結構描述](../core/media/bts-sf-queryresult.jpg "BTS_SF_QueryResult")  
  
3.  將變更儲存至結構描述。  
  
## <a name="create-message-variables-for-queryrequest-and-queryresult-schemas"></a>建立訊息變數 QueryRequest 和 QueryResult 結構描述  
 您已建立的 QueryRequest 與 QueryResult 結構描述之後，您必須建立兩個訊息變數來代表兩個訊息類型的協調流程中。  
  
#### <a name="to-create-message-variables"></a>建立訊息變數  
  
1.  開啟**NotificationService.odx**協調流程，在 [協調流程] 檢視中，加入兩個新的訊息。 設定訊息名稱，做為`QueryRequestMsg`和`QueryResultMsg`。  
  
2.  設定訊息類型**QueryRequestMsg**為**BtsSalesforceIntegration.QueryRequest**。  
  
3.  設定訊息類型**QueryResultMsg**為**BtsSalesforceIntegration.QueryResult**。  
  
4.  將變更儲存至協調流程。  
  
## <a name="update-the-orchestration-to-send-message-to-salesforce-and-receive-a-response"></a>更新協調流程以傳送訊息至 Salesforce 並接收回應  
 主題中的 <<c0> [ 步驟 3a： 到 BizTalk Server 接收 Salesforce 商機通知](../core/step-3a-receive-salesforce-opportunity-notification-into-biztalk-server.md)，我們建立了協調流程接收來自 Salesforce 的商機通知和傳送通知。 在此步驟中，我們會建置此協調流程將查詢要求傳送至 Salesforce 以取得商機相關的產品詳細資料，並接收回應。 我們已經在此步驟中建立的結構描述 （QueryRequest.xsd 和 QueryResult.xsd） 和我們將使用的訊息變數 （QueryRequestMsg 和 QueryResultMsg）。  
  
#### <a name="to-send-a-query-request-to-salesforce-and-receive-a-response"></a>以查詢要求傳送至 Salesforce 並接收回應  
  
1.  新增 建構訊息 」 圖形之後**SendNotificationAck**圖形。 設定圖形的名稱`ConstructQuery`並設定**建構的訊息**屬性**QueryRequestMsg**。  
  
2.  內**ConstructQuery**圖形中新增**轉換**圖形。 按兩下以開啟 [轉換組態] 對話方塊的 [轉換] 圖形。 在對話方塊中，選取**現有對應**選項，然後再從下拉式清單選取**BtsSalesforceIntegration.Notification_QueryRequest**。 設定**來源**至**NotificaitonMessage**，**目的地**至**QueryRequestMsg**，然後按一下 **確定**.  
  
3.  內**ConstructQuery**圖形，在 [轉換] 圖形之後新增 「 訊息指派 」 圖形。 按兩下訊息指派 」 圖形，並加入下列運算式：  
  
    ```  
    QueryRequestMsg(BtsSalesforceIntegration.PropertySchema.Query) = QueryRequestMsg.Query;  
    ```  
  
     如此一來，我們傳遞的值為**查詢**中的項目**QueryRequestMsg**結構描述升級項目**查詢**屬性結構描述中。 在設定 Wcf-webhttp 連接埠時，我們會使用這個項目，以動態方式將傳遞查詢值給要求訊息。  
  
4.  之後**ConstructQuery**圖形中新增 「 傳送 」 圖形。 命名圖形`SendQueryRequest`並將訊息類型做為**QueryRequestMsg**。  
  
5.  在 [傳送] 圖形之後新增 「 接收 」 圖形並將它命名`ReceiveQueryResult`。 設定圖形的訊息類型**QueryResultMsg**。  
  
6.  新增連接埠來傳送至 Salesforce 的查詢要求並接收回應的查詢結果。 在連接埠組態精靈中，選取下列選項：  
  
    -   將連接埠名稱指定為`SalesforceRESTInterface`。  
  
    -   選取 建立新的連接埠類型。  
  
    -   設定**通訊模式**至*要求-回應*。  
  
    -   設定**連接埠通訊方向**至*我要傳送要求並接收回應*並設定**連接埠繫結**至*指定更新*.  
  
     連接**要求**「 傳送 」 圖形的連接埠的作業 (*SendQueryRequest*) 和**回應**作業的 「 接收 」 圖形的連接埠 (*ReceiveQueryResult*)。 下列螢幕擷取畫面說明代表查詢要求傳送到 Salesforce 並接收回應的程序的協調流程的一部分。  
  
     ![傳送查詢到 Salesforce 並接收回應](../core/media/bts-sf-sendqueryrequestorch.jpg "BTS_SF_SendQueryRequestOrch")  
  
 本主題中，我們已更新的協調流程傳送至 Salesforce 的查詢要求和接收到有關有機會在 Salesforce 中建立更多詳細資料 （例如產品、 數量、 等等）。 在後續主題中，我們將會更新此解決方案，以在內部部署 SQL Server 資料庫中輸入 Salesforce 回應。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3： 建立 Visual Studio 中的 BizTalk Server 解決方案](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)