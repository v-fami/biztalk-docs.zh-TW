---
title: "使用 WCF 服務模型的 SAP 中接收輸入的 tRFC 呼叫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tRFC calls, receiving inbound using the WCF service model
- WCF service model, receiving inbound tRFC calls
ms.assetid: 02dc282b-b659-466a-8bd1-f400a05f71ec
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7fb2091d0701831985a1975aa33bd5ecb667b443
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="receive-inbound-trfc-calls-in-sap-using-the-wcf-service-model"></a>使用 WCF 服務模型的 SAP 中接收輸入的 tRFC 呼叫
您可以使用[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]為交易式 RFC (tRFC) 伺服器從 SAP 接收輸入的 tRFC 呼叫。 針對傳入的 tRFCs[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援多個 tRFCs 中的工作 (LUW) 相同的 SAP 邏輯單元。  
  
 本主題中的各節提供有關如何使用配接器做為 tRFC 伺服器 WCF 服務模型中的資訊。  
  
 您可以找到有關使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]為 tRFC 伺服器中的下列主題：  
  
-   如需 tRFCs 上支援的概觀[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱[tRFCs SAP 中的作業](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)。 繼續之前，您應該閱讀本主題。  
  
-   如需 tRFC 伺服器作業的訊息結構描述的詳細資訊，請參閱[tRFCs SAP 中的作業](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)。  
  
## <a name="the-wcf-service-contract-for-a-trfc"></a>TRFC 之 WCF 服務合約  
 您使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生您想要從 SAP 系統接收 tRFCs WCF 服務合約。 產生輸入的 tRFC 是類似於針對傳入的 RFC 產生的合約之處在於：  
  
-   tRFC 作業便會顯示一個 TRFC 節點下。  
  
-   WCF 服務合約 （介面） 的內送 tRFCs 產生名為"Trfc"。 當您將服務端點加入至服務主機，您必須指定此介面。 這也是 WCF 服務必須實作的介面。  
  
    ```  
    public interface Trfc {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.Sap/2007/03/Trfc/) of message Z_RFC_MKD_ADDRequest does not match the default value (http://Microsoft.LobServices.Sap/2007/03/)  
        [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.LobServices.Sap/2007/03/Trfc/Z_RFC_MKD_ADD", ReplyAction="http://Microsoft.LobServices.Sap/2007/03/Trfc/Z_RFC_MKD_ADD/response")]  
        Z_RFC_MKD_ADDResponse Z_RFC_MKD_ADD(Z_RFC_MKD_ADDRequest request);  
    }  
    ```  
  
-   TRFC 作業的要求訊息合約都具有 GUID 參數。 這是對應至 SAP TID tRFC 的 GUID。 TRFC 伺服器作業中，配接器會管理所有的呼叫認可、 復原，並確認 TID SAP 系統，所以沒有理由要明確地使用此 GUID。 不過，可以用它來擷取從 SAP TID[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]藉由呼叫**SapAdapterUtilities.ConvertGuidToTid**。 這可協助您疑難排解 SAP 系統上的問題。  
  
    ```  
    [System.Diagnostics.DebuggerStepThroughAttribute()]  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
    [System.ServiceModel.MessageContractAttribute(WrapperName="Z_RFC_MKD_ADD", WrapperNamespace="http://Microsoft.LobServices.Sap/2007/03/Trfc/", IsWrapped=true)]  
    public partial class Z_RFC_MKD_ADDRequest {  
  
        ...  
  
        public Z_RFC_MKD_ADDRequest(string DEST, System.Nullable<int> X, System.Nullable<int> Y, System.Guid TransactionalRfcOperationIdentifier) {  
            this.DEST = DEST;  
            this.X = X;  
            this.Y = Y;  
            this.TransactionalRfcOperationIdentifier = TransactionalRfcOperationIdentifier;  
        }  
    }  
  
    ```  
  
## <a name="how-do-i-enable-the-adapter-to-act-as-a-trfc-server"></a>如何為 tRFC 伺服器中啟用 Act 配接器？  
 若要啟用配接器做為 tRFC 伺服器，您必須設定**TidDatabaseConnectionString**屬性繫結至 TID 資料庫的連接字串。 開啟服務主機之前，您應該這麼做。 這是配接器會儲存每個 tRFC SAP 交易識別碼 (TID) 資料庫。 如需此繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。  
  
## <a name="how-do-i-enlist-in-the-transaction-for-inbound-trfcs"></a>如何將在輸入 tRFCs 的交易中編列？  
 SAP 邏輯單元的工作 (LUW) 可以包含多個 tRFCs。 SAP 系統上 LUW 識別的唯一交易識別碼 (TID)。 配接器會針對每一個 SAP 系統時它會叫用的介面卡上 tRFC 呼叫使用 TIDs 建立可認可的交易。 當 SAP 系統叫用的介面卡; tRFC配接器會與 SAP TID 到您的服務相關聯的異動流動。 您可以存取此交易成為環境交易作業方法內。 在此環境異動中登記，在作業中執行的動作便可以參與 SAP LUW。  
  
 若要在作業方法中的環境異動中登記，您必須：  
  
1.  使用作業方法加上註解**TransactionScopeRequired**屬性**OperationBehavior**屬性。 這會告知 WCF 您想要從作業內的環境交易存取。  
  
2.  建立交易範圍加上附註與操作方法**TransactionAutoComplete**屬性**OperationBehavior**屬性或明確地使用**TransactionScope**作業方法內。  
  
 下列範例會示範實作兩個作業的服務。 這兩種作業的方法必須標註**TransactionScopeRequired**屬性來存取環境交易。  
  
-   **Z_TRFC_EXAMPLE1**明確登記在交易中使用**TransactionScope**物件。  
  
-   **Z_TRFC_EXAMPLE2**附註**TransactionAutoComplete**登記在交易中的屬性  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, UseSynchronizationContext = false)]  
class Z_Example_ServiceContractClass : Trfc  
{  
  
    // This operation method explicitly creates a TransactionScope to enlist in the ambient transaction  
    // You must explictly call ts.Complete to complete the transaction before you return from the operation  
    // Otherwise the transaction is aborted.  
    // You can throw an exception or return without calling ts.complete to abort the transacation  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public Z_TRFC_EXAMPLE1Response Z_TRFC_EXAMPLE1(Z_TRFC_EXAMPLE1Request request)  
    {  
        using (TransactionScope ts = new TransactionScope(TransactionScopeOption.Required))  
        {  
            // Process tRFC  
  
            ...  
  
            Z_TRFC_EXAMPLE1Response response = new Z_TRFC_EXAMPLE1Response();  
            response.TransactionalRfcOperationIdentifier = request.TransactionalRfcOperationIdentifier;  
            return response;  
            //since there is no ts.Complete(), this is equivalent to a rollback.  
        }  
    }  
  
    // This operation method sets the TransactionAutoComplete property of the OperationBehavior attribute  
    // to enlist in the transaction. There is no need to explictly create a TransactionScope in the code.  
    // If the method returns with no unhandled exceptions, the transaction completes; otherwise it aborts  
    // You can throw an exception to abort the transaction.  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public Z_TRFC_EXAMPLE2Response Z_TRFC_EXAMPLE2(Z_TRFC_EXAMPLE2Request request)  
    {  
        // Process tRFC  
  
        ...  
  
        Z_TRFC_EXAMPLE2Response response = new Z_TRFC_EXAMPLE2Response();  
        response.TransactionalRfcOperationIdentifier = request.TransactionalRfcOperationIdentifier;  
        return response;  
        //if there is no unhandled exception, the transaction completes when the operation returns.  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
[開發應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)