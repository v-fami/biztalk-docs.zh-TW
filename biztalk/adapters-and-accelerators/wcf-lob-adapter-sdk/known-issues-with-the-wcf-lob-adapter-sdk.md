---
title: WCF LOB Adapter SDK 的已知問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2cda4248-2efa-4e3d-a5ce-9a57728c51e1
caps.latest.revision: 35
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d718450dfd4db1fd6d695c1a3ecc21f9f1fd8deb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968004"
---
# <a name="known-issues-with-the-wcf-lob-adapter-sdk"></a>WCF LOB Adapter SDK 的已知的問題
本主題描述與相關聯的已知的問題[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 它也會提供部分這些問題的解決方式。  
  
## <a name="unable-to-change-sdk-features-using-add-or-remove-programs"></a>無法變更 SDK 功能，使用 新增或移除程式
 **問題**： 使用**新增或移除程式**控制台 中，若要變更的功能失敗[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]執行 Windows Vista 的電腦上。  
  
 **解析**： 而不要使用**新增或移除程式**若要修改您的安裝，請重新執行的 Setup.exe 程式。  
  
## <a name="base-runtime"></a>基底的執行階段  
  
### <a name="applications-using-transactions-in-asynchronous-proxy-must-explicitly-call-proxyopen"></a>使用非同步 Proxy 中的交易的應用程式必須明確地呼叫 Proxy.Open  
 **問題**： 交易使用非同步 proxy 中的配接器的應用程式必須明確地呼叫 proxy。開啟以便流動的交易。  
  
 **解析**： 這可以完成後所產生 proxy[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]中用戶端程式，如下所示：  
  
```  
EchoAdapterClient echoAdapterProxy = new EchoAdapterClient("mEchoConfiguration");  
echoAdapterProxy.Open();  
...  
```  
  
### <a name="iduplexchannel-shape-not-supported"></a>不支援 IDuplexChannel 圖形  
 **問題**: IDuplexChannel 通道不支援此版本中。  
  
 **解析**： 使用 WCF 通道模型來建立 WCF 自訂繫結支援雙工通道。  
  
### <a name="request-schema-generated-with-or-without-in-or-out-parameters"></a>要求結構描述產生含 In 或 Out 參數  
 **問題**： 在**ExportInputXmlSchema**類別方法**OperationMetadata**，一律產生要求結構描述，即使它不能包含任何 in 或 out 參數。  
  
### <a name="providing-multiple-operation-namespaces"></a>提供多個作業的命名空間  
 **問題**： 如果配接器開發人員提供一項作業群組的多個作業命名空間[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]會產生不正確的 WSDL。 產生的輸入和輸出訊息部分，每個作業將不會連結至正確的結構描述參考。  
  
 **解析**： 請確定每個 OperationMetadata.OperationGroup 對應至單一 OperationMetadata.OperationNamespace。  
  
### <a name="overloaded-operations-not-supported"></a>不支援多載的作業  
 **問題**： 在本版中，動態的合約產生器 （WSDL 產生器） 元件的 sdk 不支援多載的作業，也就是作業使用相同名稱但不同的簽章。  
  
### <a name="fault-contract-not-supported"></a>不支援的錯誤合約  
 **問題**： 在此版本中，動態合約產生器 （WSDL 產生器） 元件的 sdk 不支援錯誤合約中繼資料。  
  
### <a name="failure-when-receiving-messages"></a>接收訊息時失敗  
 **問題**： 接收時，所以配接器時處理特定訊息，如果失敗的可能**接收逾時**繫結屬性設定為較小的值。 傳回的錯誤是特定配接器。  
  
 **因應措施**： 設定**接收逾時**屬性繫結至較大的值，例如 23:59:59，這最大值。  
  
### <a name="adapter-stalls-during-message-processing"></a>訊息處理期間的介面卡拖延  
 **問題**： 如果有大量的配接器的要求，處理的工作項目可能會看似延滯。  
  
 當開啟新連接，配接器佇列會由.NET 執行緒集區處理的工作項目。 一旦開啟連接時，進一步工作項目都會進入佇列來處理每個訊息。 如果執行緒集區已用完，死結可能發生封鎖要求，開啟新連接來處理訊息的要求。  
  
 **解析**： 最後會逾時要求並處理會繼續進行，但是建議的解決方式是減少要處理或增加執行緒集區中的執行緒數目的訊息數目。  
  
 若要增加的執行緒數目，修改的值[ProcessModelSection.MaxWorkerThreads 屬性](https://msdn.microsoft.com/library/system.web.configuration.processmodelsection.maxworkerthreads.aspx)。  
  
## <a name="design-time-proxy-and-schema-generation-tools"></a>設計階段 Proxy 和結構描述產生工具  
  
### <a name="limitations-with-select-contract-type"></a>使用選取的合約類型的限制  
 **問題**: 「 選取的合約型別 」 篩選套用至類別目錄樹狀結構，以及可用作業的清單。 如果配接器取用者會選取包含傳入和傳出作業類別目錄節點，全部都將會是 WSDL 和產生的 proxy，不論 「 選取的合約型別 」 篩選的一部分。  
  
 **解析**： 選取個別的作業，而非選取整個類別。  
  
### <a name="error-with-add-adapter-service-reference-visual-studio-plug-in"></a>錯誤與新增配接器服務參考 Visual Studio 外掛程式  
 **問題**： 在 BizTalk 專案在 Visual Studio 中，如果已經使用所產生 proxy [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，從相同的配接器產生另一個 proxy，則會產生此錯誤:"命名空間 '\<全域命名空間\>' 已經包含 '{合約 name}' 的定義當編譯專案。 」  
  
 此版本中不允許編輯的 proxy。  
  
 **解析**: BizTalk 專案中移除多餘的 proxy 檔案。 如果其他作業要包含在產生的 proxy，請刪除 proxy 檔案，並使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]搜尋或瀏覽中繼資料，並重新產生 proxy。  
  
### <a name="error-with-consume-adapter-service-biztalk-project-add-in"></a>錯誤與使用配接器服務 BizTalk 專案增益集  
 **問題**： 如同先前的問題，在 BizTalk 專案在 Visual Studio 中，如果從產生的結構描述中的一般類型存在[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，所以無法編譯 BizTalk 專案。  
  
 **解析**: BizTalk 專案中移除多餘的 XML 結構描述檔案、 搜尋或瀏覽所需的中繼資料，使用 取用配接器服務參考和重新產生新的 XML 結構描述檔案。  
  
### <a name="error-with-rootnode-typename-in-biztalk-projects"></a>RootNode TypeName 在 BizTalk 專案中的錯誤  
 **問題**： 在 Visual Studio 中，如果從產生的結構描述在 BizTalk 專案[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]包含無效的字元或保留的字的**RootNode TypeName**屬性，在會發生下列錯誤編譯時間: 「 節點\<參照節點\>-指定這個根節點的有效.NET 類型名稱。  此根節點的目前的.NET 類型名稱無效 （是 BizTalk 保留的關鍵字或無效 C# 識別項）。  
  
 **解析**： 選取錯誤中參考的根節點，然後在內容中，移除任何不合法的字元或保留的字從**RootNode TypeName**屬性。  
  
### <a name="metadata-generation-tool-limitations"></a>中繼資料產生工具限制  
 **問題**： 如果配接器開發人員提供在 XML 結構描述結構 OperationMetadata 及/或 TypeMetadata 衍生的類別，以及 XML 結構描述包含所略過或禁止 DataContractSerializer，中繼資料建構產生工具退而使用 XmlSerializer 進行序列化。  
  
 **解析**： 移除禁止的建構結構描述，或使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]中繼資料物件模型來產生符合與 DataContractSerializer XML 結構描述定義。  
  
### <a name="binding-name-property-does-not-take-effect"></a>繫結 Name 屬性不會生效  
 **問題**： 變更繫結名稱屬性上**繫結屬性一般** 索引標籤**新增配接器服務參考**對話方塊不會生效。  
  
 **解析**： 使用 AdapterBinding 衍生類別，以變更名稱，如下所示：  
  
```  
[Browsable(false)]  
public new virtual string Name  
{  
     set  
     {  
          base.Name = value;  
     }  
     get  
     {  
          return base.Name;  
     }  
}  
```  
  
### <a name="timeout-when-retrieving-metadata"></a>擷取中繼資料時的逾時  
 **問題**： 如果配接器包含許多作業，您可能會遇到逾時擷取中繼資料，例如使用工具時[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，WCF 配接器服務開發精靈或[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]如果您嘗試擷取在許多作業一次。  
  
 **解析**： 減少選取的作業數目。  
  
### <a name="avoid-generating-schemas-which-reference-an-external-import"></a>避免參考外部的匯入的產生結構描述  
 **問題**： 您應該避免產生包含一或多個參考外部匯入的結構描述。 如果進行此設定，將不遵守外部連結。  
  
## <a name="setup"></a>安裝程式  
  
### <a name="setup-halts-while-checking-disk-space"></a>安裝程式會檢查磁碟空間時中止  
 **問題**： 安裝時[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，您可能會收到一個對話方塊，顯示安裝程式正在檢查可用磁碟空間，以及安裝程式無法繼續。  
  
 **解析**： 發生這個問題時，您可以透過執行無訊息安裝的暫時解決此問題[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]在命令提示字元。 例如：  
  
```  
Msiexec.exe /package AdapterFramework.msi /qr  
```  
  
### <a name="biztalk-server-developer-tools-required"></a>所需的 BizTalk Server 開發人員工具  
 **問題**： 當目標系統具有 Visual Studio 和 Microsoft BizTalk Server 開發人員工具不[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]安裝程式將會失敗。 這是因為它要求必須在電腦上，才能安裝 BizTalk Server 開發人員工具[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。  
  
 **解析**： 請務必在目標電腦已安裝使用開發人員工具，才能安裝 BizTalk Server [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。  
  
### <a name="corrupt-biztalk-server-installation-causes-sdk-to-fail"></a>BizTalk Server 項目安裝失敗的 SDK 已損毀  
 **問題**: BizTalk Server 的損毀的安裝可能會造成的 SDK 安裝失敗，發生下列錯誤: 「 DirectoryNotFound 例外狀況 」。  
  
 **解析**： 解除安裝再重新安裝 BizTalk Server。  
  
 
## <a name="see-also"></a>請參閱  
 [BizTalk Server 使用者入門](../../core/getting-started-with-biztalk-server.md)