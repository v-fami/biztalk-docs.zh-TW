---
title: 如何部署自訂的配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f17b336c-6232-4889-ab7e-92b83fab0f5f
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e36443b99f01688a38e66a4a302ab64bb220092f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22250294"
---
# <a name="how-to-deploy-a-custom-adapter"></a>如何部署自訂配接器
完整的配接器安裝程序包含下列步驟：  
  
1.  檢查 相依性。 例如，MSMQ 配接器安裝程式會檢查本機 MSMQ 服務是否存在，因為配接器執行階段需要該服務。  
  
2.  安裝本機檔案系統。 這包括建立安裝資料夾，並複製二進位檔案和支援檔案。 確認對資料夾與檔案存取權限的存取設定正確。  
  
3.  將 Managed 組件安裝至系統全域組件快取。  
  
4.  建立配接器的登錄機碼。  
  
    > [!NOTE]
    >  如果是 32 位元配接器，「BizTalk Server 管理主控台」會使用登錄中的 HKEY_CLASSES_ROOT 分支來取得自訂配接器組態。  如果 32 位元的配接器是安裝在 64 位元的伺服器上，則「BizTalk Server 管理主控台」會改用 HKEY_CLASSES_ROOT\Wow6432Node\ 分支來取得配接器組態資料。  
  
5.  將配接器新增至 BizTalk Server。 這表示在 BizTalk 管理資料庫中新增配接器以及反映配接器所升級之屬性的屬性結構描述的項目。 這項步驟有時候是使用「BizTalk Server 管理主控台」手動進行。  
  
## <a name="exceptions"></a>例外狀況  
 在部分的 BizTalk Server 安裝過程中，配接器安裝程式可能不需要檢查相依性。 例如，在僅含安裝管理工具的安裝中，配接器安裝程式不需要檢查配接器執行階段相依性，因為沒有使用配接器執行階段。 同樣的情況也適用於僅含執行階段的 BizTalk Server 安裝，在這種安裝中，配接器安裝程式不需要檢查配接器設計階段相依性。  
  
 在多個 BizTalk Server 環境中，上述清單的最後一個步驟 (將配接器加入 BizTalk Server) 只有當配接器安裝在第一部 BizTalk Server 時才會發生。 這是因為所有的 BizTalk Server 服務執行個體共用相同的 BizTalk 管理資料庫 (使用預設名稱 BizTalkMgmtDB)。 如果將配接器加入相同群組的其他 BizTalk 伺服器中，將無法進行最後一個步驟。  
  
## <a name="install-the-adapter-assemblies-into-the-global-assembly-cache"></a>將配接器組件安裝至全域組件快取  
 為了支援不同配接器安裝路徑的多個 BizTalk Server 主控件環境，配接器組件必須安裝在系統全域組件快取中。  
  
 在配接器安裝與組態期間，新的配接器項目會建立於 BizTalk 管理資料庫 (預設名稱為 BizTalkMgmtDB) 的 adm_adapter 表中。 此項目包含所有 BizTalk Server 在執行階段與設計階段所使用的參照資訊。  
  
 **InBoundAssemblyPath**和**OutboundAssemblyPath**欄位用於 BizTalk Server 執行階段找出載入配接器二進位檔的位置。 由於一個 BizTalk Server 群組中只有一個 BizTalk 管理資料庫，群組裡所有 BizTalk 伺服器都必須共用此資訊。 如果您想要將配接器安裝在群組中的其他 BizTalk 伺服器上，您必須在這些伺服器上使用相同的安裝路徑。 如果本機安裝路徑與 BizTalk 管理資料庫的安裝路徑不同，則 BizTalk Server 無法載入配接器二進位檔。  
  
 請務必以強式名稱為配接器組件簽章，並在配接器安裝期間使用 Gacutil.exe 將配接器組件放置到系統全域組件快取。 請確定您保留**InBoundAssemblyPath**和**OutboundAssemblyPath** null 或空的欄位。  
  
## <a name="using-the-framework-for-adapter-configuration"></a>使用配接器組態架構  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供為配接器組態使用者介面 (UI) 產生內容頁的機制。 這個機制是基於組態屬性的 XML 結構描述 (XSD) 定義。 使用這個架構對配接器開發人員來說是一大挑戰。 本節提供其中一些問題有效的解決方法。  
  
### <a name="consider-custom-property-editors-for-all-your-key-properties"></a>考慮為您所有的機碼屬性使用自訂屬性編輯器  
 重要的屬性驗證無法置於內容頁中的屬性之上。 這個架構嘗試使用 XML 結構描述 (XSD) simpleType 限制來定義 UI 的驗證規則， 套用最大與最小值的簡單規則，但是不支援字串欄位的規則運算式限制。 此外，在套用限制之前，資料會轉換為 Common Language Runtime (CLR) 類型。 這表示 UI 的使用者有時候會看到隱密的類型轉換錯誤，而不是超出範圍的錯誤。 總之，驗證邏輯非常薄弱。  
  
 許多配接器開發人員所採用的解決方案是撰寫自訂的屬性編輯器來編輯內容頁上的主要屬性。 如果有一些交互相依的屬性 (經常出現這種情況)，則自訂屬性編輯器可以將結果併入單一欄位，而後執行階段可以分隔它們。 雖然十分簡單，但這是將必要的自訂程式碼加入介面的唯一方式 。  
  
 撰寫自訂屬性編輯器是比較直接的方法，並且可以為 XSD 屬性加上使用編輯器的註解。 註解會參照公開屬性編輯器進入點的組件，並加上程式碼以顯示 CLR 表單。 現在您將可以撰寫一般使用者介面，並使用 Visual Studio 所提供給您的傳統介面產生工具。  
  
 下列程式碼將顯示如何使用 XSD 來新增自訂屬性編輯器：  
  
```  
<xs:element name="queueDetails" type="xs:string" minOccurs="0">  
    <xs:annotation>  
        <xs:appinfo>  
           <baf:designer>  
               <baf:displayname _locID="queueName">Queue Definition</baf:displayname>  
               <baf:description _locID="receiveQueueDesc">Details of MQSeries Server, Queue Manager and Queue from where you want to receive messages.</baf:description>  
               <baf:category _locID="mqsCategory">MQSeries</baf:category>  
               <baf:editor assembly="Microsoft.BizTalk Server.Adapter.MQSAdmin.dll">Microsoft.BizTalk Server.Adapter.MQSAdmin.MQSUITypeEditor</baf:editor>  
            </baf:designer>  
        </xs:appinfo>  
    </xs:annotation>  
</xs:element>  
  
```  
  
 所參照的程式碼應如下所示：  
  
```  
public class MQSUITypeEditor : System.Drawing.Design.UITypeEditor  
{  
public override System.Drawing.Design.UITypeEditorEditStyle GetEditStyle  
(System.ComponentModel.ITypeDescriptorContext context)   
{  
return System.Drawing.Design.UITypeEditorEditStyle.Modal;  
}  
public override object EditValue (System.ComponentModel.ITypeDescriptorContext context,  
System.IServiceProvider provider, object value)   
{  
Form qdForm = new QueueDefinitionForm(value);  
IWindowsFormsEditorService service =   
(IWindowsFormsEditorService)provider.GetService(typeof(IWindowsFormsEditorService));  
DialogResult dialogResult = service.ShowDialog(qdForm);  
//…  
}  
}  
class QueueDefinitionForm : System.Windows.Forms.Form   
{  
//  traditional UI code goes here!  
}  
  
```  
  
 管理執行階段必須能夠找到  XSD 所參照的組件，因此您應該將組件加入全域組件快取中。