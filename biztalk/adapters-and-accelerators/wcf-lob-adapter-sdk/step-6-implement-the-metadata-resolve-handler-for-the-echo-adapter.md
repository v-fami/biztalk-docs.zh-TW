---
title: 步驟 6： 實作中繼資料解析的處理常式回應配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0105d1b0-efbd-457b-af0d-08e29408a318
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 022da31cacedaa59c9e5821fb049165f463c7f06
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22226998"
---
# <a name="step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter"></a><span data-ttu-id="708bf-102">步驟 6： 實作回應配接器中繼資料解析處理常式</span><span class="sxs-lookup"><span data-stu-id="708bf-102">Step 6: Implement the Metadata Resolve Handler for the Echo Adapter</span></span>
<span data-ttu-id="708bf-103">![步驟 6 的 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-6of9.gif "Step_6of9")</span><span class="sxs-lookup"><span data-stu-id="708bf-103">![Step 6 of 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-6of9.gif "Step_6of9")</span></span>  
  
 <span data-ttu-id="708bf-104">**若要完成的時間：** 45 分鐘的時間</span><span class="sxs-lookup"><span data-stu-id="708bf-104">**Time to complete:** 45 minutes</span></span>  
  
 <span data-ttu-id="708bf-105">在此步驟中，您會實作`Microsoft.ServiceModel.Channels.Common.IMetadataResolverHandler`介面，以解析作業和輸入回應配接器中繼資料。</span><span class="sxs-lookup"><span data-stu-id="708bf-105">In this step, you implement the `Microsoft.ServiceModel.Channels.Common.IMetadataResolverHandler` interface to resolve operation and type metadata for the echo adapter.</span></span> <span data-ttu-id="708bf-106">不論您的配接器的功能，您必須實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="708bf-106">Regardless of your adapter's capability, you must implement this interface.</span></span> <span data-ttu-id="708bf-107">[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]會自動產生為您呼叫 EchoAdapterMetadataResolverHandler 的衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="708bf-107">The [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] automatically generates the derived class called EchoAdapterMetadataResolverHandler for you.</span></span>  
  
 <span data-ttu-id="708bf-108">在下列區段中，您可以更新 EchoAdapterMetadataResolverHandler 類別，以取得更了解如何實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="708bf-108">In the following section, you update the EchoAdapterMetadataResolverHandler class to get a better understanding on how to implement this interface.</span></span> <span data-ttu-id="708bf-109">當您完成此步驟中時，您必須解決回應配接器處理常式工作中繼資料。</span><span class="sxs-lookup"><span data-stu-id="708bf-109">When you complete this step, you have a working metadata resolve handler for the echo adapter.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="708bf-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="708bf-110">Prerequisites</span></span>  
 <span data-ttu-id="708bf-111">在開始此步驟之前，您必須已順利完成[步驟 5： 回應配接器實作中繼資料的搜尋處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="708bf-111">Before you begin this step, you must have successfully completed [Step 5: Implement the Metadata Search Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md).</span></span> <span data-ttu-id="708bf-112">您也必須了解下列的作業和型別類別：</span><span class="sxs-lookup"><span data-stu-id="708bf-112">You must also understand the following operation and type classes:</span></span>  
  
-   `Microsoft.ServiceModel.Channels.Common.ParameterizedOperationMetadata`  
  
-   `Microsoft.ServiceModel.Channels.Common.OperationMetadata`  
  
-   `Microsoft.ServiceModel.Channels.Common.OperationParameter`  
  
-   `Microsoft.ServiceModel.Channels.Common.OperationResult`  
  
-   `Microsoft.ServiceModel.Channels.Common.TypeMetadata`  
  
-   `Microsoft.ServiceModel.Channels.Common.StructuredTypeMetadata`  
  
-   `Microsoft.ServiceModel.Channels.Common.TypeMember`  
  
-   `Microsoft.ServiceModel.Channels.Common.SimpleQualifiedType`  
  
-   `Microsoft.ServiceModel.Channels.Common.ComplexQualifiedType`  
  
## <a name="the-imetadataresolverhandler-interface"></a><span data-ttu-id="708bf-113">IMetadataResolverHandler 介面</span><span class="sxs-lookup"><span data-stu-id="708bf-113">The IMetadataResolverHandler Interface</span></span>  
  
```  
public interface IMetadataResolverHandler : IConnectionHandler, IDisposable  
  {  
      bool IsOperationMetadataValid(string operationId, DateTime lastUpdatedTimestamp, TimeSpan timeout);        
      bool IsTypeMetadataValid(string typeId, DateTime lastUpdatedTimestamp, TimeSpan timeout);  
      OperationMetadata ResolveOperationMetadata(string operationId, TimeSpan timeout, out TypeMetadataCollection extraTypeMetadataResolved);  
      TypeMetadata ResolveTypeMetadata(string typeId, TimeSpan timeout, out TypeMetadataCollection extraTypeMetadataResolved);  
  }  
```  
  
 <span data-ttu-id="708bf-114">下表說明每個方法的用途：</span><span class="sxs-lookup"><span data-stu-id="708bf-114">The following table describes what each method does:</span></span>  
  
|<span data-ttu-id="708bf-115">**方法名稱**</span><span class="sxs-lookup"><span data-stu-id="708bf-115">**Method Name**</span></span>|<span data-ttu-id="708bf-116">**說明**</span><span class="sxs-lookup"><span data-stu-id="708bf-116">**Description**</span></span>|  
|---------------------|---------------------|  
|<span data-ttu-id="708bf-117">IsOperationMetadataValid</span><span class="sxs-lookup"><span data-stu-id="708bf-117">IsOperationMetadataValid</span></span>|<span data-ttu-id="708bf-118">如果指定的時間與日期後尚未變更的類型中繼資料，則傳回 true</span><span class="sxs-lookup"><span data-stu-id="708bf-118">Returns a true if the type metadata has not changed since the date and time specified</span></span>|  
|<span data-ttu-id="708bf-119">IsTypeMetadataValid</span><span class="sxs-lookup"><span data-stu-id="708bf-119">IsTypeMetadataValid</span></span>|<span data-ttu-id="708bf-120">傳回布林值，指出指定的型別中繼資料是否有效。</span><span class="sxs-lookup"><span data-stu-id="708bf-120">Returns a Boolean value that indicates whether the specified type metadata is valid.</span></span>|  
|<span data-ttu-id="708bf-121">ResolveOperationMetadata</span><span class="sxs-lookup"><span data-stu-id="708bf-121">ResolveOperationMetadata</span></span>|<span data-ttu-id="708bf-122">解析成對應的作業識別碼`Microsoft.ServiceModel.Channels.Common.OperationMetadata`</span><span class="sxs-lookup"><span data-stu-id="708bf-122">Resolves an operation ID to corresponding `Microsoft.ServiceModel.Channels.Common.OperationMetadata`</span></span>|  
|<span data-ttu-id="708bf-123">ResolveTypeMetadata</span><span class="sxs-lookup"><span data-stu-id="708bf-123">ResolveTypeMetadata</span></span>|<span data-ttu-id="708bf-124">提供的中繼資料 typeId 解析成對應`Microsoft.ServiceModel.Channels.Common.TypeMetadata`。</span><span class="sxs-lookup"><span data-stu-id="708bf-124">Resolves a supplied metadata typeId to a corresponding `Microsoft.ServiceModel.Channels.Common.TypeMetadata`.</span></span>|  
  
### <a name="to-implement-the-isoperationmetadatavalid-method"></a><span data-ttu-id="708bf-125">若要實作 IsOperationMetadataValid 方法</span><span class="sxs-lookup"><span data-stu-id="708bf-125">To implement the IsOperationMetadataValid method</span></span>  
  
1.  <span data-ttu-id="708bf-126">在 [方案總管] 中，按兩下**EchoAdapterMetadataResolverHandler.cs**檔案。</span><span class="sxs-lookup"><span data-stu-id="708bf-126">In Solution Explorer, double-click the **EchoAdapterMetadataResolverHandler.cs** file.</span></span>  
  
2.  <span data-ttu-id="708bf-127">在 Visual Studio 編輯器中，以滑鼠右鍵按一下任何位置內編輯器] 的內容功能表，指向**大綱**，然後按一下 [**取消大綱**。</span><span class="sxs-lookup"><span data-stu-id="708bf-127">In the Visual Studio editor, right-click anywhere within the editor, in the context menu, point to **Outlining**, and then click **Stop Outlining**.</span></span>  
  
3.  <span data-ttu-id="708bf-128">在 Visual Studio 編輯器中，尋找**IsOperationMetadataValid**方法，在這個方法，取代現有的下列單一陳述式，表示每個指定的作業中繼資料有效。</span><span class="sxs-lookup"><span data-stu-id="708bf-128">In the Visual Studio editor, find the **IsOperationMetadataValid** method, inside this method, replace the existing with the following single statement to indicate that every specified operation metadata is valid.</span></span>  
  
    ```csharp  
    return true;  
    ```  
  
### <a name="to-implement-the-istypemetadatavalid-method"></a><span data-ttu-id="708bf-129">若要實作 IsTypeMetadataValid 方法</span><span class="sxs-lookup"><span data-stu-id="708bf-129">To implement the IsTypeMetadataValid method</span></span>  
  
-   <span data-ttu-id="708bf-130">在 Visual Studio 編輯器中，尋找**IsTypeMetadataValid**方法，在這個方法，取代現有的下列單一陳述式，表示每個指定的型別中繼資料有效。</span><span class="sxs-lookup"><span data-stu-id="708bf-130">In the Visual Studio editor, find the **IsTypeMetadataValid** method, inside this method, replace the existing with the following single statement to indicate that every specified type metadata is valid.</span></span>  
  
    ```csharp  
    return true;  
    ```  
  
### <a name="to-implement-the-resolveoperationmetadata-method"></a><span data-ttu-id="708bf-131">若要實作 ResolveOperationMetadata 方法</span><span class="sxs-lookup"><span data-stu-id="708bf-131">To implement the ResolveOperationMetadata method</span></span>  
  
1.  <span data-ttu-id="708bf-132">在 Visual Studio 編輯器中，尋找**ResolveOperationMetadata**方法，在這個方法，取代現有以下列解析 OnReceiveEcho 作業，void OnReceiveEcho （Uri 的路徑，長 fileLength）。</span><span class="sxs-lookup"><span data-stu-id="708bf-132">In the Visual Studio editor, find the **ResolveOperationMetadata** method, inside this method, replace the existing with the following to resolve the OnReceiveEcho operation, void OnReceiveEcho(Uri path, long fileLength).</span></span>  
  
    ```csharp  
    extraTypeMetadataResolved = null;  
    switch( operationId )  
    {  
        case "Echo/OnReceiveEcho":  
            ParameterizedOperationMetadata om = new ParameterizedOperationMetadata(operationId, "OnReceiveEcho");  
            om.OriginalName = "lobNotification";  
            om.Description = "This operation echoes the location and length of a file dropped in the specified file system.";  
            om.OperationGroup = "EchoInboundContract";  
            om.OperationNamespace = EchoAdapter.SERVICENAMESPACE;  
            // syntax: void OnReceiveEcho(Uri path, long fileLength)  
            OperationParameter parmPath = new OperationParameter("path", OperationParameterDirection.In, QualifiedType.UriType, false);  
            parmPath.Description = "Absolute path of the file";  
            OperationParameter parmLength = new OperationParameter("length", OperationParameterDirection.In, QualifiedType.LongType, false);  
            parmLength.Description = "Length of the file received in this location.";  
            om.Parameters.Add(parmPath);  
            om.Parameters.Add(parmLength);  
            om.OperationResult = OperationResult.Empty;  
            return om;  
    ```  
  
2.  <span data-ttu-id="708bf-133">繼續加入下列內容以解決 Echo/EchoStrings 作業，string [] EchoStrings(string data)。</span><span class="sxs-lookup"><span data-stu-id="708bf-133">Continue adding the following to resolve the Echo/EchoStrings operation, string[] EchoStrings(string data).</span></span>  
  
    ```csharp  
    case "Echo/EchoStrings":  
        om = new ParameterizedOperationMetadata(operationId, "EchoStrings");  
        om.OriginalName = "lobEchoStrings";  
        om.Description = "This operation echoes the incoming string COUNT number of times in a string array.";  
        om.OperationGroup = "EchoOutboundContract";  
        om.OperationNamespace = EchoAdapter.SERVICENAMESPACE;  
        // syntax: string[] EchoStrings(string data)  
        OperationParameter parmData = new OperationParameter("data", OperationParameterDirection.In, QualifiedType.StringType, false);  
        parmData.Description = "Input string";  
        om.Parameters.Add(parmData);  
        om.OperationResult = new OperationResult(QualifiedType.StringType, true);  
        return om;  
    ```  
  
3.  <span data-ttu-id="708bf-134">繼續加入下列的邏輯，以解決 Echo/EchoStrings 作業，string [] EchoStrings(string data)。</span><span class="sxs-lookup"><span data-stu-id="708bf-134">Continue adding the following logic to resolve the Echo/EchoStrings operation, string[] EchoStrings(string data).</span></span>  
  
    ```csharp  
    case "Echo/EchoGreetings":  
        om = new ParameterizedOperationMetadata(operationId, "EchoGreetings");  
        om.OriginalName = "lobEchoGreetings";  
        om.Description = "This operation echoes the incoming Greeting object COUNT number of times in an array of type Greeting.";  
        om.OperationGroup = "EchoOutboundContract";  
        om.OperationNamespace = EchoAdapter.SERVICENAMESPACE;  
        // syntax: Greeting[] EchoGreetings(Greeting greeting)  
        ComplexQualifiedType cqtGreeting = new ComplexQualifiedType("Types/GreetingType");  
        OperationParameter parmGreeting = new OperationParameter("greeting", OperationParameterDirection.In, cqtGreeting, false);  
        parmGreeting.Description = "Input greeting";  
        om.Parameters.Add(parmGreeting);  
        om.OperationResult = new OperationResult(cqtGreeting, true);  
        return om;  
    ```  
  
4.  <span data-ttu-id="708bf-135">繼續加入下列的邏輯，以解決 CustomGreeting EchoCustomGreetingFromFile(Uri greetingInstancePath) 作業。</span><span class="sxs-lookup"><span data-stu-id="708bf-135">Continue adding the following logic to resolve the CustomGreeting EchoCustomGreetingFromFile(Uri greetingInstancePath) operation.</span></span>  
  
    ```csharp  
    case "Echo/EchoCustomGreetingFromFile":  
        om = new ParameterizedOperationMetadata(operationId, "EchoCustomGreetingFromFile");  
        om.OriginalName = "lobEchoGreetingUsePredefinedMetadata";  
        om.Description = "This operation echoes the incoming Greeting object COUNT number of times in an array of type Greeting.  The Greeting type metadata is created using predefined XSD file.";  
        om.OperationGroup = "EchoOutboundContract";  
        om.OperationNamespace = EchoAdapter.SERVICENAMESPACE;  
        OperationParameter parmGreetingInstancePath = new OperationParameter("greetingInstancePath", OperationParameterDirection.In, QualifiedType.UriType, false);  
        om.Parameters.Add(parmGreetingInstancePath);  
        ComplexQualifiedType cqtGreetingXsd = new ComplexQualifiedType("Types/CustomGreetingFromXsdType");  
        om.OperationResult = new OperationResult(cqtGreetingXsd, false);  
  
        // resolve extra typemetadata here  
        extraTypeMetadataResolved = new TypeMetadataCollection();  
  
        // use a predefined schema to generate metadata for this type  
        CustomGreetingTypeMetadata tmGreetingXsd = new CustomGreetingTypeMetadata("Types/CustomGreetingFromXsdType", "CustomGreeting");  
        extraTypeMetadataResolved.Add(tmGreetingXsd);                   
        return om;  
  
    ```  
  
5.  <span data-ttu-id="708bf-136">繼續加入下列命令來處理預設的情況。</span><span class="sxs-lookup"><span data-stu-id="708bf-136">Continue adding the following to handle default case.</span></span>  
  
    ```csharp  
        default:  
            throw new AdapterException("Cannot resolve metadata for operation identifier " + operationId);  
    }  
    ```  
  
### <a name="to-implement-the-resolvetypemetadata-method"></a><span data-ttu-id="708bf-137">若要實作 ResolveTypeMetadata 方法</span><span class="sxs-lookup"><span data-stu-id="708bf-137">To implement the ResolveTypeMetadata method</span></span>  
  
-   <span data-ttu-id="708bf-138">在 Visual Studio 編輯器中，尋找**ResolveTypeMetadata**方法，在這個方法，取代下列傳回現有`Microsoft.ServiceModel.Channels.Common.TypeMetadata`物件。</span><span class="sxs-lookup"><span data-stu-id="708bf-138">In the Visual Studio editor, find the **ResolveTypeMetadata** method, inside this method, replace the existing with the following to return a `Microsoft.ServiceModel.Channels.Common.TypeMetadata` object.</span></span>  
  
    ```csharp  
    extraTypeMetadataResolved = null;  
    string typeNamespaceForGreeting = EchoAdapter.SERVICENAMESPACE + "/Types";  
    switch (typeId)  
    {  
        case "Types/GreetingType":  
            StructuredTypeMetadata tmGreeting = new StructuredTypeMetadata(typeId, "Greeting");  
            tmGreeting.TypeNamespace = typeNamespaceForGreeting;  
            tmGreeting.Members.Add(new TypeMember("id", QualifiedType.GuidType, false));  
            tmGreeting.Members.Add(new TypeMember("sentDateTime", QualifiedType.DateTimeType, false));  
            ComplexQualifiedType cqtName = new ComplexQualifiedType("Types/NameType");  
            tmGreeting.Members.Add(new TypeMember("name", cqtName, false));  
            tmGreeting.Members.Add(new TypeMember("greetingText", QualifiedType.StringType, false));  
            return tmGreeting;  
  
        case "Types/NameType":  
            StructuredTypeMetadata tmName = new StructuredTypeMetadata(typeId, "Name");  
            tmName.TypeNamespace = typeNamespaceForGreeting;  
            ComplexQualifiedType cqtSalutation = new ComplexQualifiedType("Types/SalutationType");  
            tmName.Members.Add(new TypeMember("salutation", cqtSalutation, false));  
            tmName.Members.Add(new TypeMember("firstName", QualifiedType.StringType, false));  
            tmName.Members.Add(new TypeMember("middleName", QualifiedType.StringType, false));  
            tmName.Members.Add(new TypeMember("lastName", QualifiedType.StringType, false));  
            return tmName;  
  
        case "Types/SalutationType":  
            EnumTypeMetadata tmSalutation = new EnumTypeMetadata(typeId, "Salutation", new string[] { "Mr.", "Mrs.", "Dr.", "Ms.", "Miss" });  
            tmSalutation.TypeNamespace = typeNamespaceForGreeting;  
            return tmSalutation;  
  
        default:  
            throw new AdapterException("Cannot resolve metadata for type identifier " + typeId);  
    }  
  
    ```  
  
### <a name="to-define-the-custom-greeting-type-metadata-class"></a><span data-ttu-id="708bf-139">若要定義自訂問候語類型中繼資料類別</span><span class="sxs-lookup"><span data-stu-id="708bf-139">To define the custom greeting type metadata class</span></span>  
  
1.  <span data-ttu-id="708bf-140">在 方案總管 中，以滑鼠右鍵按一下**回應配接器**專案，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="708bf-140">In Solution Explorer, right-click the **Echo Adapter** project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="708bf-141">在**加入新項目**對話方塊的 **範本**，按一下 **類別**。</span><span class="sxs-lookup"><span data-stu-id="708bf-141">In the **Add New Item** dialog box, under **Templates**, click **Class**.</span></span>  
  
3.  <span data-ttu-id="708bf-142">在**名稱**文字方塊中，輸入**CustomGreetingTypeMetadata**。</span><span class="sxs-lookup"><span data-stu-id="708bf-142">In the **Name** text box, type **CustomGreetingTypeMetadata**.</span></span>  
  
4.  <span data-ttu-id="708bf-143">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="708bf-143">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="708bf-144">在 Visual Studio 編輯器中，以下列內容取代現有的程式碼：</span><span class="sxs-lookup"><span data-stu-id="708bf-144">In the Visual Studio editor, replace the existing code with the following:</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using Microsoft.ServiceModel.Channels.Common;  
    using System.Xml;  
    using System.Xml.Schema;  
    using System.IO;  
  
    namespace Microsoft.Adapters.Samples.EchoV2  
    {  
        public class CustomGreetingTypeMetadata : TypeMetadata  
        {  
            private const string CONST_METADATA_FILE_NAME = "Microsoft.Adapters.Samples.EchoV2.CustomGreeting.xsd";  
  
            public CustomGreetingTypeMetadata(string typeId, string typeName)  
                : base(typeId, typeName)  
            {  
                this.TypeNamespace = EchoAdapter.SERVICENAMESPACE + "/PreDefinedTypes";  
                this.Description = " ";  
                this.CanUseCommonCache = true;  
                // if the nillable is not set to true, the generated proxy wraps the operation  
                // with request and response objects  
                this.IsNillable = true;  
            }  
  
            /// <summary>  
            /// Override the base ExportXmlSchema to provide own   
            /// custom XML Schema  
            /// </summary>  
            /// <param name="schemaExportContext"></param>  
            /// <param name="metadataLookup"></param>  
            /// <param name="timeout"></param>  
            public override void ExportXmlSchema(XmlSchemaExportContext schemaExportContext, MetadataLookup metadataLookup, TimeSpan timeout)  
            {  
                if (schemaExportContext == null)  
                {  
                    throw new AdapterException("Schema export context is null.");  
                }  
                // Read in XML Schema file or create XmlSchema object yourself  
                Stream predefinedXsdFile = System.Reflection.Assembly.GetExecutingAssembly().GetManifestResourceStream(CONST_METADATA_FILE_NAME);  
                XmlReader reader = XmlReader.Create(predefinedXsdFile);  
                XmlSchema schema = XmlSchema.Read(reader, null);  
                if (!IsComplexTypeAlreadyDefined(schemaExportContext.SchemaSet, schema))  
                {  
                    schemaExportContext.SchemaSet.Add(schema);  
                    if (!schemaExportContext.NamespacePrefixSet.ContainsKey(this.TypeNamespace))  
                    {  
                        schemaExportContext.NamespacePrefixSet.Add(this.TypeNamespace, getUniqueNamespacePrefix(schemaExportContext, 0));  
                    }  
                }  
                reader.Close();  
            }  
  
            /// <summary>  
            /// A default value cannot be set for this type metadata.  
            /// </summary>  
            public override bool CanSetDefaultValue  
            {  
                get { return false; }  
            }  
  
            /// <summary>  
            /// Helper function to see if the schema is already defined in the   
            /// XmlSchemaSet.  
            /// </summary>  
            /// <param name="oldschemaset"></param>  
            /// <param name="newschema"></param>  
            /// <returns></returns>  
            public static bool IsComplexTypeAlreadyDefined(XmlSchemaSet oldschemaset, XmlSchema newschema)  
            {  
                // ensure correct namespace was defined in the passed-in schema  
                foreach (XmlSchema schema in oldschemaset.Schemas(newschema.TargetNamespace))  
                {  
                    foreach (XmlSchemaObject newschemaObject in newschema.Items)  
                    {  
                        if (newschemaObject is XmlSchemaComplexType)  
                        {  
                            //check for the definition of complex type in the schemaset             
                            foreach (XmlSchemaObject schemaObject in schema.Items)  
                            {  
                                XmlSchemaComplexType complexType = schemaObject as XmlSchemaComplexType;  
                                // Definition of this Complex Type already exists  
                                if (complexType != null && String.Compare(complexType.Name, ((XmlSchemaComplexType)newschemaObject).Name, false, System.Globalization.CultureInfo.InvariantCulture) == 0)  
                                    return true;  
                            }  
                        }  
                    }  
                }  
                return false;  
            }  
  
            /// <summary>  
            /// Helper function to generate a unique namespace prefix  
            /// </summary>  
            /// <param name="schemaExportContext"></param>  
            /// <param name="startSuffix"></param>  
            /// <returns></returns>  
            private string getUniqueNamespacePrefix(XmlSchemaExportContext schemaExportContext, int startSuffix)  
            {  
                string defaultPrefix = "ns";  
                string val = defaultPrefix + startSuffix;  
                if (schemaExportContext.NamespacePrefixSet.ContainsValue(val))  
                {  
                    return getUniqueNamespacePrefix(schemaExportContext, ++startSuffix);  
                }  
                else  
                {  
                    return val;  
                }  
            }  
        }  
    }  
    ```  
  
6.  <span data-ttu-id="708bf-145">在 Visual Studio 中，從**檔案**功能表上，按一下 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="708bf-145">In Visual Studio, from the **File** menu, click **Save All**.</span></span>  
  
### <a name="to-create-the-custom-greeting-xml-schema-definition"></a><span data-ttu-id="708bf-146">若要建立自訂問候語 XML 結構描述定義</span><span class="sxs-lookup"><span data-stu-id="708bf-146">To create the custom greeting XML schema definition</span></span>  
  
1.  <span data-ttu-id="708bf-147">在 方案總管 中，以滑鼠右鍵按一下**回應配接器**專案，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="708bf-147">In Solution Explorer, right-click the **Echo Adapter** project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="708bf-148">在**加入新項目**對話方塊的 **範本**，按一下  **XML 結構描述**。</span><span class="sxs-lookup"><span data-stu-id="708bf-148">In the **Add New Item** dialog box, under **Templates**, click **XML Schema**.</span></span>  
  
3.  <span data-ttu-id="708bf-149">在**名稱**文字方塊中，輸入**CustomGreeting**。</span><span class="sxs-lookup"><span data-stu-id="708bf-149">In the **Name** text box, type **CustomGreeting**.</span></span>  
  
4.  <span data-ttu-id="708bf-150">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="708bf-150">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="708bf-151">在 [方案總管] 中，以滑鼠右鍵按一下**CustomGreeting.xsd**檔案，然後選擇**檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="708bf-151">In Solution Explorer, right-click the **CustomGreeting.xsd** file and choose **View Code**.</span></span>  
  
6.  <span data-ttu-id="708bf-152">在 Visual Studio 編輯器中，開始開始 CustomGreeting 結構描述定義為下列程式碼取代現有的程式碼：</span><span class="sxs-lookup"><span data-stu-id="708bf-152">In the Visual Studio editor, begin by replacing the existing code with the following code that begins the definition of the CustomGreeting schema:</span></span>  
  
    ```csharp  
    <?xml version="1.0" encoding="utf-8" ?>   
    <xs:schema id="XMLSchema1"   
                      targetNamespace="http://tempuri.org/XMLSchema1.xsd"  
                      elementFormDefault="qualified"  
                      xmlns="http://tempuri.org/XMLSchema1.xsd"  
                      xmlns:mstns="http://tempuri.org/XMLSchema1.xsd"  
                      xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    </xs:schema>  
    ```  
  
     <span data-ttu-id="708bf-153">下列程式碼開始 CustomGreeting 結構描述定義：</span><span class="sxs-lookup"><span data-stu-id="708bf-153">with the following code that begins the definition of the CustomGreeting schema:</span></span>  
  
    ```csharp  
    <?xml version="1.0" encoding="utf-16"?>  
    <xsd:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns="echov2://microsoft.adapters.samples.echov2/PreDefinedTypes" elementFormDefault="qualified" targetNamespace="echov2://microsoft.adapters.samples.echov2/PreDefinedTypes" xmlns:xsd ="http://www.w3.org/2001/XMLSchema">  
    ```  
  
7.  <span data-ttu-id="708bf-154">將下列內容加入定義 CustomGreeting 項目：</span><span class="sxs-lookup"><span data-stu-id="708bf-154">Add the following to define the CustomGreeting element:</span></span>  
  
    ```csharp  
    <xsd:element name="greeting" type="CustomGreeting" />  
    ```  
  
8.  <span data-ttu-id="708bf-155">現在加入 CustomGreeting 複雜類型的定義：</span><span class="sxs-lookup"><span data-stu-id="708bf-155">Now add the definition of the CustomGreeting complex type:</span></span>  
  
    ```csharp  
    <xsd:complexType name="CustomGreeting">  
      <xsd:sequence>  
        <xsd:element name="address" type="UsAddress" />  
        <xsd:element name="greetingText" type="xsd:string" />  
      </xsd:sequence>  
    </xsd:complexType>  
    ```  
  
9. <span data-ttu-id="708bf-156">繼續 CustomGreeting 結構描述定義加入 UsAddress 複雜類型：</span><span class="sxs-lookup"><span data-stu-id="708bf-156">Continue the CustomGreeting schema definition by adding the  UsAddress complex type:</span></span>  
  
    ```csharp  
    <xsd:complexType name="UsAddress">  
      <xsd:sequence>  
        <xsd:element minOccurs="1" maxOccurs="1" name="street1" nillable="true" type="xsd:string" />  
        <xsd:element minOccurs="0" maxOccurs="1" name="street2" type="xsd:string" />  
        <xsd:element minOccurs="1" maxOccurs="1" name="city" type="xsd:string" />  
        <xsd:element minOccurs="1" maxOccurs="1" name="state" type="xsd:string" />  
        <xsd:element name="zip" type="PostalCode" />  
      </xsd:sequence>  
    </xsd:complexType>  
    ```  
  
10. <span data-ttu-id="708bf-157">加入 PostalCode 簡單型別和結尾標記之結構描述，以完成 CustomGreeting 結構描述定義：</span><span class="sxs-lookup"><span data-stu-id="708bf-157">Complete the definition of the CustomGreeting schema by adding the PostalCode simple type and the closing tag for the schema:</span></span>  
  
    ```csharp  
      <xsd:simpleType name="PostalCode">  
        <xsd:restriction base="xsd:positiveInteger">  
          <xsd:pattern value="\d{5}" />  
        </xsd:restriction>  
      </xsd:simpleType>  
    </xsd:schema>  
    ```  
  
11. <span data-ttu-id="708bf-158">現在更新此檔案的建置動作，因此它會被視為內嵌的資源。</span><span class="sxs-lookup"><span data-stu-id="708bf-158">Now update the build action for this file so it is treated as an embedded resource.</span></span> <span data-ttu-id="708bf-159">若要這樣做，在 Visual Studio 方案] 窗格中，以滑鼠右鍵按一下檔案，然後選擇 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="708bf-159">To do this, in the Visual Studio solution pane, right-click the file and choose **Properties**.</span></span> <span data-ttu-id="708bf-160">變更 建置動作從**無**至**內嵌資源**。</span><span class="sxs-lookup"><span data-stu-id="708bf-160">Change Build Action from **None** to **Embedded Resource**.</span></span>  
  
12. <span data-ttu-id="708bf-161">在 Visual Studio 中，從**檔案**功能表上，按一下 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="708bf-161">In Visual Studio, from the **File** menu, click **Save All**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="708bf-162">您應該已經儲存您的工作結果。</span><span class="sxs-lookup"><span data-stu-id="708bf-162">You saved your work.</span></span> <span data-ttu-id="708bf-163">您可以安全地關閉目前的 Visual Studio 或移至下一個步驟中，[步驟 7： 回應配接器實作同步輸出的處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="708bf-163">You can safely close Visual Studio at this time or go to the next step, [Step 7: Implement the Synchronous Outbound Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter.md).</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="708bf-164">我剛剛做什麼？</span><span class="sxs-lookup"><span data-stu-id="708bf-164">What Did I Just Do?</span></span>  
 <span data-ttu-id="708bf-165">您只實作中繼資料解析回應配接器的功能。</span><span class="sxs-lookup"><span data-stu-id="708bf-165">You just implemented the metadata resolving capability for the echo adapter.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="708bf-166">後續步驟</span><span class="sxs-lookup"><span data-stu-id="708bf-166">Next Steps</span></span>  
 <span data-ttu-id="708bf-167">在下一個步驟中，您會實作同步輸出的處理常式回應配接器。</span><span class="sxs-lookup"><span data-stu-id="708bf-167">In the next step, you implement the synchronous outbound handler for the Echo Adapter.</span></span> <span data-ttu-id="708bf-168">您接著實作同步輸入處理常式，然後建立及部署回應配接器。</span><span class="sxs-lookup"><span data-stu-id="708bf-168">You then implement the synchronous inbound handler and then build and deploy the Echo Adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="708bf-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="708bf-169">See Also</span></span>  
 <span data-ttu-id="708bf-170">[步驟 5： 回應配接器實作的中繼資料搜尋處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="708bf-170">[Step 5: Implement the Metadata Search Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-5-implement-the-metadata-search-handler-for-the-echo-adapter.md) </span></span>  
 <span data-ttu-id="708bf-171">[步驟 7： 回應配接器實作同步輸出的處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="708bf-171">[Step 7: Implement the Synchronous Outbound Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter.md) </span></span>  
 [<span data-ttu-id="708bf-172">教學課程 1： 在開發回應配接器</span><span class="sxs-lookup"><span data-stu-id="708bf-172">Tutorial 1: Develop the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)