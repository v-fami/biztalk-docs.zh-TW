---
title: "如何部署自訂的配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f17b336c-6232-4889-ab7e-92b83fab0f5f
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e36443b99f01688a38e66a4a302ab64bb220092f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-deploy-a-custom-adapter"></a><span data-ttu-id="79b5b-102">如何部署自訂配接器</span><span class="sxs-lookup"><span data-stu-id="79b5b-102">How to Deploy a Custom Adapter</span></span>
<span data-ttu-id="79b5b-103">完整的配接器安裝程序包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="79b5b-103">A complete adapter installation process consists of the following steps:</span></span>  
  
1.  <span data-ttu-id="79b5b-104">檢查 相依性。</span><span class="sxs-lookup"><span data-stu-id="79b5b-104">Check dependencies.</span></span> <span data-ttu-id="79b5b-105">例如，MSMQ 配接器安裝程式會檢查本機 MSMQ 服務是否存在，因為配接器執行階段需要該服務。</span><span class="sxs-lookup"><span data-stu-id="79b5b-105">For example, the MSMQ adapter installer checks for the existence of the local MSMQ service because the adapter runtime depends on it.</span></span>  
  
2.  <span data-ttu-id="79b5b-106">安裝本機檔案系統。</span><span class="sxs-lookup"><span data-stu-id="79b5b-106">Set up the local file system.</span></span> <span data-ttu-id="79b5b-107">這包括建立安裝資料夾，並複製二進位檔案和支援檔案。</span><span class="sxs-lookup"><span data-stu-id="79b5b-107">This includes creating installation folders and copying binary and support files.</span></span> <span data-ttu-id="79b5b-108">確認對資料夾與檔案存取權限的存取設定正確。</span><span class="sxs-lookup"><span data-stu-id="79b5b-108">Ensure access to folders and file access permissions are configured properly.</span></span>  
  
3.  <span data-ttu-id="79b5b-109">將 Managed 組件安裝至系統全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="79b5b-109">Install managed assemblies into the system global assembly cache.</span></span>  
  
4.  <span data-ttu-id="79b5b-110">建立配接器的登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="79b5b-110">Create registry keys for the adapter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="79b5b-111">如果是 32 位元配接器，「BizTalk Server 管理主控台」會使用登錄中的 HKEY_CLASSES_ROOT 分支來取得自訂配接器組態。</span><span class="sxs-lookup"><span data-stu-id="79b5b-111">For a 32-bit adapter, the BizTalk Server Administration Console uses the HKEY_CLASSES_ROOT branch in the registry to obtain custom adapter configuration.</span></span>  <span data-ttu-id="79b5b-112">如果 32 位元的配接器是安裝在 64 位元的伺服器上，則「BizTalk Server 管理主控台」會改用 HKEY_CLASSES_ROOT\Wow6432Node\ 分支來取得配接器組態資料。</span><span class="sxs-lookup"><span data-stu-id="79b5b-112">If a 32-bit adapter is installed on a 64-bit server, the BizTalk Serve Administration Console instead uses the HKEY_CLASSES_ROOT\Wow6432Node\ branch for adapter configuration data.</span></span>  
  
5.  <span data-ttu-id="79b5b-113">將配接器新增至 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="79b5b-113">Add the adapter to BizTalk Server.</span></span> <span data-ttu-id="79b5b-114">這表示在 BizTalk 管理資料庫中新增配接器以及反映配接器所升級之屬性的屬性結構描述的項目。</span><span class="sxs-lookup"><span data-stu-id="79b5b-114">This means new entries in the BizTalk Management database for the adapter as well as for the property schema used to reflect properties the adapter promotes.</span></span> <span data-ttu-id="79b5b-115">這項步驟有時候是使用「BizTalk Server 管理主控台」手動進行。</span><span class="sxs-lookup"><span data-stu-id="79b5b-115">This step is sometimes done manually using the BizTalk Server Administration console.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="79b5b-116">例外狀況</span><span class="sxs-lookup"><span data-stu-id="79b5b-116">Exceptions</span></span>  
 <span data-ttu-id="79b5b-117">在部分的 BizTalk Server 安裝過程中，配接器安裝程式可能不需要檢查相依性。</span><span class="sxs-lookup"><span data-stu-id="79b5b-117">The adapter installer may not need to check the dependencies in partial BizTalk Server installations.</span></span> <span data-ttu-id="79b5b-118">例如，在僅含安裝管理工具的安裝中，配接器安裝程式不需要檢查配接器執行階段相依性，因為沒有使用配接器執行階段。</span><span class="sxs-lookup"><span data-stu-id="79b5b-118">For example, in an administration tools-only installation, the adapter installer does not need to check adapter runtime dependencies because the adapter runtime is not used.</span></span> <span data-ttu-id="79b5b-119">同樣的情況也適用於僅含執行階段的 BizTalk Server 安裝，在這種安裝中，配接器安裝程式不需要檢查配接器設計階段相依性。</span><span class="sxs-lookup"><span data-stu-id="79b5b-119">The same is true in the BizTalk Server runtime-only installation, where the adapter installer does not need to check the adapter design-time dependencies.</span></span>  
  
 <span data-ttu-id="79b5b-120">在多個 BizTalk Server 環境中，上述清單的最後一個步驟 (將配接器加入 BizTalk Server) 只有當配接器安裝在第一部 BizTalk Server 時才會發生。</span><span class="sxs-lookup"><span data-stu-id="79b5b-120">In multiple BizTalk Server environments, the last step in the preceding list (Add the adapter to BizTalk Server) only happens in the adapter installation on the first BizTalk Server.</span></span> <span data-ttu-id="79b5b-121">這是因為所有的 BizTalk Server 服務執行個體共用相同的 BizTalk 管理資料庫 (使用預設名稱 BizTalkMgmtDB)。</span><span class="sxs-lookup"><span data-stu-id="79b5b-121">This is because all BizTalk Server service instances share the same BizTalk Management database (with the default name, BizTalkMgmtDB).</span></span> <span data-ttu-id="79b5b-122">如果將配接器加入相同群組的其他 BizTalk 伺服器中，將無法進行最後一個步驟。</span><span class="sxs-lookup"><span data-stu-id="79b5b-122">If adapters are added to other BizTalk servers in the same group, the additional steps fail.</span></span>  
  
## <a name="install-the-adapter-assemblies-into-the-global-assembly-cache"></a><span data-ttu-id="79b5b-123">將配接器組件安裝至全域組件快取</span><span class="sxs-lookup"><span data-stu-id="79b5b-123">Install the Adapter Assemblies into the Global Assembly Cache</span></span>  
 <span data-ttu-id="79b5b-124">為了支援不同配接器安裝路徑的多個 BizTalk Server 主控件環境，配接器組件必須安裝在系統全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="79b5b-124">To support multiple BizTalk Server host environments with different adapter installation paths, the adapter assemblies must be installed into the system global assembly cache.</span></span>  
  
 <span data-ttu-id="79b5b-125">在配接器安裝與組態期間，新的配接器項目會建立於 BizTalk 管理資料庫 (預設名稱為 BizTalkMgmtDB) 的 adm_adapter 表中。</span><span class="sxs-lookup"><span data-stu-id="79b5b-125">During the adapter installation and configuration, a new adapter entry is created in the adm_adapter table of the BizTalk Management database (with the default name BizTalkMgmtDB).</span></span> <span data-ttu-id="79b5b-126">此項目包含所有 BizTalk Server 在執行階段與設計階段所使用的參照資訊。</span><span class="sxs-lookup"><span data-stu-id="79b5b-126">This entry contains all reference information used by BizTalk Server for both run time and design time.</span></span>  
  
 <span data-ttu-id="79b5b-127">**InBoundAssemblyPath**和**OutboundAssemblyPath**欄位用於 BizTalk Server 執行階段找出載入配接器二進位檔的位置。</span><span class="sxs-lookup"><span data-stu-id="79b5b-127">The **InBoundAssemblyPath** and **OutboundAssemblyPath** fields are used by the BizTalk Server runtime to find out where to load the adapter binaries.</span></span> <span data-ttu-id="79b5b-128">由於一個 BizTalk Server 群組中只有一個 BizTalk 管理資料庫，群組裡所有 BizTalk 伺服器都必須共用此資訊。</span><span class="sxs-lookup"><span data-stu-id="79b5b-128">Because there is only one BizTalk Management database for a BizTalk Server group, all BizTalk servers in the group must share this same piece of information.</span></span> <span data-ttu-id="79b5b-129">如果您想要將配接器安裝在群組中的其他 BizTalk 伺服器上，您必須在這些伺服器上使用相同的安裝路徑。</span><span class="sxs-lookup"><span data-stu-id="79b5b-129">If you want to install the adapter on different BizTalk servers within the group, you must use the same installation path on each of those servers.</span></span> <span data-ttu-id="79b5b-130">如果本機安裝路徑與 BizTalk 管理資料庫的安裝路徑不同，則 BizTalk Server 無法載入配接器二進位檔。</span><span class="sxs-lookup"><span data-stu-id="79b5b-130">If the local installation path is different from the path stored in the BizTalk Management database, BizTalk Server cannot load the adapter binaries.</span></span>  
  
 <span data-ttu-id="79b5b-131">請務必以強式名稱為配接器組件簽章，並在配接器安裝期間使用 Gacutil.exe 將配接器組件放置到系統全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="79b5b-131">Always sign the adapter's assembly with a strong name and use Gacutil.exe to put the adapter assembly into the system global assembly cache during the adapter installation.</span></span> <span data-ttu-id="79b5b-132">請確定您保留**InBoundAssemblyPath**和**OutboundAssemblyPath** null 或空的欄位。</span><span class="sxs-lookup"><span data-stu-id="79b5b-132">Make sure that you leave the **InBoundAssemblyPath** and **OutboundAssemblyPath** fields null, or empty.</span></span>  
  
## <a name="using-the-framework-for-adapter-configuration"></a><span data-ttu-id="79b5b-133">使用配接器組態架構</span><span class="sxs-lookup"><span data-stu-id="79b5b-133">Using the Framework for Adapter Configuration</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="79b5b-134"> 提供為配接器組態使用者介面 (UI) 產生內容頁的機制。</span><span class="sxs-lookup"><span data-stu-id="79b5b-134"> provides a mechanism for generating property sheets for the adapter configuration user interface (UI).</span></span> <span data-ttu-id="79b5b-135">這個機制是基於組態屬性的 XML 結構描述 (XSD) 定義。</span><span class="sxs-lookup"><span data-stu-id="79b5b-135">It is based on an XML Schema Definition (XSD) definition of the configuration properties.</span></span> <span data-ttu-id="79b5b-136">使用這個架構對配接器開發人員來說是一大挑戰。</span><span class="sxs-lookup"><span data-stu-id="79b5b-136">The use of this framework introduces significant challenges for the adapter developer.</span></span> <span data-ttu-id="79b5b-137">本節提供其中一些問題有效的解決方法。</span><span class="sxs-lookup"><span data-stu-id="79b5b-137">This section suggests an effective workaround for some of these issues.</span></span>  
  
### <a name="consider-custom-property-editors-for-all-your-key-properties"></a><span data-ttu-id="79b5b-138">考慮為您所有的機碼屬性使用自訂屬性編輯器</span><span class="sxs-lookup"><span data-stu-id="79b5b-138">Consider Custom Property Editors for all Your Key Properties</span></span>  
 <span data-ttu-id="79b5b-139">重要的屬性驗證無法置於內容頁中的屬性之上。</span><span class="sxs-lookup"><span data-stu-id="79b5b-139">It is impossible to put significant property validation on top of properties in the property sheet.</span></span> <span data-ttu-id="79b5b-140">這個架構嘗試使用 XML 結構描述 (XSD) simpleType 限制來定義 UI 的驗證規則，</span><span class="sxs-lookup"><span data-stu-id="79b5b-140">The framework attempts to use XML Schema Definition (XSD) simpleType restrictions to define the validation rules for the UI.</span></span> <span data-ttu-id="79b5b-141">套用最大與最小值的簡單規則，但是不支援字串欄位的規則運算式限制。</span><span class="sxs-lookup"><span data-stu-id="79b5b-141">The simple rules for maximum and minimum value are applied but the regular expression restriction for string fields is not supported.</span></span> <span data-ttu-id="79b5b-142">此外，在套用限制之前，資料會轉換為 Common Language Runtime (CLR) 類型。</span><span class="sxs-lookup"><span data-stu-id="79b5b-142">Also, the data is converted into common language runtime (CLR) types before the restriction is applied.</span></span> <span data-ttu-id="79b5b-143">這表示 UI 的使用者有時候會看到隱密的類型轉換錯誤，而不是超出範圍的錯誤。</span><span class="sxs-lookup"><span data-stu-id="79b5b-143">This means the user of the UI sometimes gets a cryptic type-conversion error rather than an out-of-range error.</span></span> <span data-ttu-id="79b5b-144">總之，驗證邏輯非常薄弱。</span><span class="sxs-lookup"><span data-stu-id="79b5b-144">All in all, the validation logic is very weak.</span></span>  
  
 <span data-ttu-id="79b5b-145">許多配接器開發人員所採用的解決方案是撰寫自訂的屬性編輯器來編輯內容頁上的主要屬性。</span><span class="sxs-lookup"><span data-stu-id="79b5b-145">The solution many adapter developers have adopted is to write custom property editors for the main properties on their property sheet.</span></span> <span data-ttu-id="79b5b-146">如果有一些交互相依的屬性 (經常出現這種情況)，則自訂屬性編輯器可以將結果併入單一欄位，而後執行階段可以分隔它們。</span><span class="sxs-lookup"><span data-stu-id="79b5b-146">If there are a number of cross-dependent properties (as is often the case), then the custom property editor can combine the results into a single field and the runtime can later separate them.</span></span> <span data-ttu-id="79b5b-147">雖然十分簡單，但這是將必要的自訂程式碼加入介面的唯一方式 。</span><span class="sxs-lookup"><span data-stu-id="79b5b-147">This is the only way to get the necessary (though still generally trivial) custom code into the interface.</span></span>  
  
 <span data-ttu-id="79b5b-148">撰寫自訂屬性編輯器是比較直接的方法，並且可以為 XSD 屬性加上使用編輯器的註解。</span><span class="sxs-lookup"><span data-stu-id="79b5b-148">Custom property editors are relatively straightforward to write and the property in the XSD can be annotated to use them.</span></span> <span data-ttu-id="79b5b-149">註解會參照公開屬性編輯器進入點的組件，並加上程式碼以顯示 CLR 表單。</span><span class="sxs-lookup"><span data-stu-id="79b5b-149">The annotation references an assembly that exposes the property editor entry point, and it is coded to show a CLR Form.</span></span> <span data-ttu-id="79b5b-150">現在您將可以撰寫一般使用者介面，並使用 Visual Studio 所提供給您的傳統介面產生工具。</span><span class="sxs-lookup"><span data-stu-id="79b5b-150">You can now write a regular user interface and use the traditional interface-generation tools that Visual Studio offers.</span></span>  
  
 <span data-ttu-id="79b5b-151">下列程式碼將顯示如何使用 XSD 來新增自訂屬性編輯器：</span><span class="sxs-lookup"><span data-stu-id="79b5b-151">The following code shows how to use the XSD to add a custom property editor:</span></span>  
  
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
  
 <span data-ttu-id="79b5b-152">所參照的程式碼應如下所示：</span><span class="sxs-lookup"><span data-stu-id="79b5b-152">The code that is referenced should look like this:</span></span>  
  
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
  
 <span data-ttu-id="79b5b-153">管理執行階段必須能夠找到  XSD 所參照的組件，因此您應該將組件加入全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="79b5b-153">The administration runtime must be able to find the assembly referenced in the XSD, so you should add it to the global assembly cache.</span></span>