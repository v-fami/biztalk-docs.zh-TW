---
title: 規劃使用 Web 服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24863069-929b-4b0b-9643-073965fb5532
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4a13151a5dd76b20b70872b963dc6a688370444
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302270"
---
# <a name="planning-for-consuming-web-services"></a><span data-ttu-id="18fa9-102">規劃使用 Web 服務</span><span class="sxs-lookup"><span data-stu-id="18fa9-102">Planning for Consuming Web Services</span></span>
<span data-ttu-id="18fa9-103">Web 服務的規劃可以分成兩個類別，規劃發佈 Web 服務，以及規劃使用 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="18fa9-103">Planning for Web services can be divided into two categories, planning for publishing Web services and planning for consuming Web services.</span></span> <span data-ttu-id="18fa9-104">本主題說明使用 Web 服務的考量。</span><span class="sxs-lookup"><span data-stu-id="18fa9-104">This topic describes the considerations for consuming Web services.</span></span> <span data-ttu-id="18fa9-105">如需發佈 Web 服務資訊，請參閱[Planning for Publishing Web Services1](../technical-guides/planning-for-publishing-web-services1.md)。</span><span class="sxs-lookup"><span data-stu-id="18fa9-105">For information about publishing Web services, see [Planning for Publishing Web Services1](../technical-guides/planning-for-publishing-web-services1.md).</span></span>  
  
 <span data-ttu-id="18fa9-106">當您建立您的計劃，請記住下列：</span><span class="sxs-lookup"><span data-stu-id="18fa9-106">Keep the following in mind as you create your plan:</span></span>  
  
-   <span data-ttu-id="18fa9-107">**在參數名稱中使用兩個底線字元**</span><span class="sxs-lookup"><span data-stu-id="18fa9-107">**Using Two Underscore Characters in a Parameter Name**</span></span>  
  
     <span data-ttu-id="18fa9-108">Web 方法的參數名稱不可以 "__" (兩個底線字元) 作為開頭。</span><span class="sxs-lookup"><span data-stu-id="18fa9-108">Parameter names for Web methods cannot begin with "__" (two underscore characters).</span></span> <span data-ttu-id="18fa9-109">以兩個底線字元作為開頭的名稱可能會建立無法為 XLANG/s 所支援 (亦即無法使用) 的 Web 訊息部分。</span><span class="sxs-lookup"><span data-stu-id="18fa9-109">Names that begin with two underscore characters may create Web message parts that are unsupported (unusable) by XLANG/s.</span></span>  
  
-   <span data-ttu-id="18fa9-110">**Any 項目與 anyAttribute 屬性不支援 Web 方法**</span><span class="sxs-lookup"><span data-stu-id="18fa9-110">**The Any Element and the anyAttribute Attributes Are Not Supported in Web Methods**</span></span>  
  
     <span data-ttu-id="18fa9-111">您無法使用**任何**項目或**anyAttribute** Web 方法的結構描述中的屬性。</span><span class="sxs-lookup"><span data-stu-id="18fa9-111">You cannot use the **any** element or **anyAttribute** attribute in the schema for a Web method.</span></span>  
  
-   <span data-ttu-id="18fa9-112">**使用 XLANG/s 關鍵字**</span><span class="sxs-lookup"><span data-stu-id="18fa9-112">**Using XLANG/s Keywords**</span></span>  
  
     <span data-ttu-id="18fa9-113">Web 服務名稱或 Web 方法名稱不能是 XLANG/s 中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="18fa9-113">A Web service name or a Web method name cannot be a keyword in an XLANG/s.</span></span> <span data-ttu-id="18fa9-114">如果在 Web 服務名稱或是 Web 方法名稱中使用 XLANG/s 關鍵字，當您新增 Web 服務時就會出現編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="18fa9-114">If you use an XLANG/s keyword in the Web service name or Web method name, you will get a compilation error when you add the Web service.</span></span> <span data-ttu-id="18fa9-115">如需 XLANG/s 語言保留字的清單，請參閱[XLANG/s 保留字](http://go.microsoft.com/fwlink/?LinkId=155765)(http://go.microsoft.com/fwlink/?LinkId=155765)。</span><span class="sxs-lookup"><span data-stu-id="18fa9-115">For a list of reserved words for the XLANG/s language, see the [XLANG/s Reserved Words](http://go.microsoft.com/fwlink/?LinkId=155765) (http://go.microsoft.com/fwlink/?LinkId=155765).</span></span>  
  
-   <span data-ttu-id="18fa9-116">**必要的 XLANG/s 支援的參數型別**</span><span class="sxs-lookup"><span data-stu-id="18fa9-116">**Required XLANG/s Support for Parameter Types**</span></span>  
  
     <span data-ttu-id="18fa9-117">使用非 XLANG/s 支援的 Web 方法參數的類型會造成編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="18fa9-117">Using non-XLANG/s supported Web method parameter types will cause compilation errors.</span></span> <span data-ttu-id="18fa9-118">例如，BizTalk Server 不支援包含結構描述類型之單一維度陣列的參數。</span><span class="sxs-lookup"><span data-stu-id="18fa9-118">For example, BizTalk Server does not support a parameter that consists of a single dimensional array of schema types.</span></span> <span data-ttu-id="18fa9-119">此外，BizTalk Server 不支援多維陣列。</span><span class="sxs-lookup"><span data-stu-id="18fa9-119">In addition, BizTalk Server does not support multidimensional arrays.</span></span> <span data-ttu-id="18fa9-120">如需在 BizTalk Server 的 XLANG/s 語言保留字的清單，請參閱[XLANG/s 保留字](http://go.microsoft.com/fwlink/?LinkId=155765)(http://go.microsoft.com/fwlink/?LinkId=155765)。</span><span class="sxs-lookup"><span data-stu-id="18fa9-120">For a list of words that XLANG/s language reserves in BizTalk Server, see [XLANG/s Reserved Words](http://go.microsoft.com/fwlink/?LinkId=155765) (http://go.microsoft.com/fwlink/?LinkId=155765).</span></span>  
  
-   <span data-ttu-id="18fa9-121">**避免加入 Web 參考包含 C# 關鍵字或識別項所造成的編譯錯誤**</span><span class="sxs-lookup"><span data-stu-id="18fa9-121">**Avoiding Compilation Errors Caused by Adding Web References Containing C# Keywords or Identifiers**</span></span>  
  
     <span data-ttu-id="18fa9-122">當您使用**加入 Web 參考**若要加入 Web 參考加入 BizTalk 專案，BizTalk Server 將會呼叫每個 Web 方法至結構描述所需的結構描述類型。</span><span class="sxs-lookup"><span data-stu-id="18fa9-122">When you use the **Add Web Reference**to add Web references to BizTalk projects, BizTalk Server converts the schema types that are required to call each Web method to schemas.</span></span> <span data-ttu-id="18fa9-123">BizTalk Server 會將這些結構描述加入到 Reference.xsd 中。</span><span class="sxs-lookup"><span data-stu-id="18fa9-123">BizTalk Server adds these schemas to Reference.xsd.</span></span> <span data-ttu-id="18fa9-124">如果您的結構描述包含 C# 關鍵字的項目名稱，或者項目名稱不是有效的 C# 識別項，便可能會產生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="18fa9-124">If your schemas contain element names that are C# keywords or the element name is not valid as a C# identifier, you may get a run-time error.</span></span> <span data-ttu-id="18fa9-125">為了避免執行階段錯誤，請確定您使用的 Web 服務不包含 C# 關鍵字項目名稱或是無效的 C# 識別項。</span><span class="sxs-lookup"><span data-stu-id="18fa9-125">To avoid run-time errors, ensure that the Web service you consume does not contain element names that are C# keywords or invalid C# identifiers.</span></span>  
  
-   <span data-ttu-id="18fa9-126">**多個服務/連接埠類型定義不受支援**</span><span class="sxs-lookup"><span data-stu-id="18fa9-126">**Multiple Service/Port Type Definitions Are Unsupported**</span></span>  
  
     <span data-ttu-id="18fa9-127">BizTalk Server 支援使用單一服務與連接埠類型定義來新增 Web 服務檔。</span><span class="sxs-lookup"><span data-stu-id="18fa9-127">BizTalk Server supports adding a Web service file with a single service and port type definition.</span></span> <span data-ttu-id="18fa9-128">如果您使用多個服務與連接埠類型定義來新增 WSDL 檔案，可能會出現下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="18fa9-128">If you add a WSDL file with multiple service or port type definitions, you may receive the following error:</span></span>  
  
     `Could not generate BizTalk files. Object reference not set to an instance of an object.`  
  
-   <span data-ttu-id="18fa9-129">**支援使用 Web 服務所公開的陣列**</span><span class="sxs-lookup"><span data-stu-id="18fa9-129">**Support for Consuming Arrays Exposed by Web Services**</span></span>  
  
     <span data-ttu-id="18fa9-130">BizTalk Server 可以使用不是 BizTalk Server Web 服務的 Web 服務所公開的一維和不規則陣列。</span><span class="sxs-lookup"><span data-stu-id="18fa9-130">BizTalk Server can consume one dimensional and jagged arrays exposed by Web services that are not BizTalk Server Web services.</span></span> <span data-ttu-id="18fa9-131">如需如何使用 Web 服務陣列的詳細資訊，請參閱[如何取用 Web 服務陣列](http://go.microsoft.com/fwlink/?LinkId=155766)(http://go.microsoft.com/fwlink/?LinkId=155766)。</span><span class="sxs-lookup"><span data-stu-id="18fa9-131">For more information about how to consume Web service arrays, see [How to Consume Web Service Arrays](http://go.microsoft.com/fwlink/?LinkId=155766) (http://go.microsoft.com/fwlink/?LinkId=155766).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="18fa9-132">不支援多維度陣列語法。</span><span class="sxs-lookup"><span data-stu-id="18fa9-132">Multi dimensional array syntax is not supported.</span></span> <span data-ttu-id="18fa9-133">例如， *MyArray [1,5]*。</span><span class="sxs-lookup"><span data-stu-id="18fa9-133">For example, *MyArray[1,5]*.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="18fa9-134">BizTalk Server 不支援使用的陣列**資料集**Web 服務所公開的物件。</span><span class="sxs-lookup"><span data-stu-id="18fa9-134">BizTalk Server does not support consuming an array of **DataSet** objects exposed by a Web service.</span></span> <span data-ttu-id="18fa9-135">XLANG/s 子服務原本即支援.NET DataSet 類別，但如果您建立 BizTalk 專案，其中包含 Web 參考加入 Web 服務會公開.NET DataSet 物件的陣列，您就會發生錯誤，當您嘗試編譯專案。</span><span class="sxs-lookup"><span data-stu-id="18fa9-135">The XLANG/s subservice does natively support the .NET DataSet class, but if you create a BizTalk project that contains a Web reference to a Web service that exposes an array of .NET DataSet objects you will get errors when you attempt to compile the project.</span></span>  
  
-   <span data-ttu-id="18fa9-136">**Web 方法參數必須是可序列化的 Xml**</span><span class="sxs-lookup"><span data-stu-id="18fa9-136">**Web Method Parameters Must be Xml Serializable**</span></span>  
  
     <span data-ttu-id="18fa9-137">在使用的 Web 服務中，所有參數都必須是可序列化的 XML。</span><span class="sxs-lookup"><span data-stu-id="18fa9-137">All parameters in a consumed Web service must be Xml Serializable.</span></span> <span data-ttu-id="18fa9-138">如果您新增的 Web 方法中，包含的參數為不可序列化的 Xml，就會產生下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="18fa9-138">If you add a Web method that contains a parameter that is not Xml Serializable, you may receive the following error message:</span></span>  
  
     <span data-ttu-id="18fa9-139">System.Xml.Element 必須是可序列化的 XML，才能做為訊息部分類型。</span><span class="sxs-lookup"><span data-stu-id="18fa9-139">System.Xml.Element must be Xml Seralizeable to be a message part type.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="18fa9-140">資料型別**XmlDocument**和**資料集**，沒有可序列化的 Xml，同時支援。</span><span class="sxs-lookup"><span data-stu-id="18fa9-140">The data types, **XmlDocument** and **DataSet**, while not Xml Serializable, are supported.</span></span>  
  
-   <span data-ttu-id="18fa9-141">**使用僅限傳訊的 Web 服務**</span><span class="sxs-lookup"><span data-stu-id="18fa9-141">**Consuming Messaging-Only Web Services**</span></span>  
  
     <span data-ttu-id="18fa9-142">取用僅限傳訊的 Web 服務時，所有的 BizTalk Server 訊息內文部分名稱必須符合 Web 方法參數名稱。</span><span class="sxs-lookup"><span data-stu-id="18fa9-142">When consuming messaging-only Web services, all BizTalk Server message body part names must match the Web method parameter names.</span></span> <span data-ttu-id="18fa9-143">例如，如果 Web 服務的簽章為 `WebMethod(MyType1 type1, MyType2 type2)`，則部分名稱必定為 type1 與 type2，且可能發生下列執行階段錯誤：</span><span class="sxs-lookup"><span data-stu-id="18fa9-143">For example, if the signature of the Web service is `WebMethod(MyType1 type1, MyType2 type2)`, the part name must be type1 and type2, you may get the following runtime error:</span></span>  
  
     `Failed to retrieve the message part for parameter %1`  
  
     <span data-ttu-id="18fa9-144">如需詳細資訊，請參閱[取用 Web 服務在 Messaging-Only 案例如何](http://go.microsoft.com/fwlink/?LinkId=155767)(http://go.microsoft.com/fwlink/?LinkId=155767)。</span><span class="sxs-lookup"><span data-stu-id="18fa9-144">For more information, see [How to Consume Web Services in a Messaging-Only Scenario](http://go.microsoft.com/fwlink/?LinkId=155767) (http://go.microsoft.com/fwlink/?LinkId=155767).</span></span>  
  
-   <span data-ttu-id="18fa9-145">**以程式設計方式設定 SOAP 傳送埠**</span><span class="sxs-lookup"><span data-stu-id="18fa9-145">**Configuring a SOAP Send Port Programmatically**</span></span>  
  
     <span data-ttu-id="18fa9-146">您可以在訊息內容中，使用程式來設定組態屬性。</span><span class="sxs-lookup"><span data-stu-id="18fa9-146">It is possible to set configuration properties programmatically on the message context.</span></span> <span data-ttu-id="18fa9-147">您可以在協調流程或自訂管線元件中設定這些屬性，是否傳送埠是靜態或動態。</span><span class="sxs-lookup"><span data-stu-id="18fa9-147">You can set these properties in an orchestration or a custom pipeline component whether the send port is static or dynamic.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="18fa9-148">若要設定**MethodName**屬性靜態 soap 傳送埠以程式設計的方式，您需要設定**方法名稱**至 **[稍後指定]** 中**Web服務** 索引標籤**SOAP 傳輸屬性**] 對話方塊 [BizTalk Server 管理主控台中的。</span><span class="sxs-lookup"><span data-stu-id="18fa9-148">To configure the **MethodName** property for the static SOAP send port programmatically, you need to set **Method name** to **[Specify Later]** in the **Web Service** tab of the **SOAP Transport Properties** dialog box in the BizTalk Server Administration console.</span></span>  
  
     <span data-ttu-id="18fa9-149">如需有關**MethodName**屬性，請參閱[如何動態設定取用 Web 服務的 URI](http://go.microsoft.com/fwlink/?LinkID=155768) (http://go.microsoft.com/fwlink/?LinkID=155768)。</span><span class="sxs-lookup"><span data-stu-id="18fa9-149">For more information about the **MethodName** property, see [How to Dynamically Set the URI of a Consumed Web Service](http://go.microsoft.com/fwlink/?LinkID=155768) (http://go.microsoft.com/fwlink/?LinkID=155768).</span></span>  
  
-   <span data-ttu-id="18fa9-150">**屬性規則**</span><span class="sxs-lookup"><span data-stu-id="18fa9-150">**Property Rules**</span></span>  
  
     <span data-ttu-id="18fa9-151">如果組態屬性是設於接收管線的協調流程或自訂管線元件中，則會套用下列規則：</span><span class="sxs-lookup"><span data-stu-id="18fa9-151">If the configuration property is set in an orchestration or in a custom pipeline component in a receive pipeline, then the following rules are applied:</span></span>  
  
    -   <span data-ttu-id="18fa9-152">若訊息傳送至靜態傳送埠，屬性值會以該傳送埠設定的值覆寫。</span><span class="sxs-lookup"><span data-stu-id="18fa9-152">If a message is sent to a static send port, the property value will be overwritten with the value configured for that send port.</span></span>  
  
    -   <span data-ttu-id="18fa9-153">若訊息傳送至動態傳送埠，則不會覆寫屬性值。</span><span class="sxs-lookup"><span data-stu-id="18fa9-153">If a message is sent to a dynamic send port, the property value will not be overwritten.</span></span>  
  
     <span data-ttu-id="18fa9-154">如果組態屬性是設於傳送管線的自訂管線元件中，則會套用下列規則：</span><span class="sxs-lookup"><span data-stu-id="18fa9-154">If a configuration property is set in a custom pipeline component in a send pipeline, then the following rule is applied:</span></span>  
  
    -   <span data-ttu-id="18fa9-155">無論訊息是傳送至靜態或動態傳送埠，都不會覆寫值。</span><span class="sxs-lookup"><span data-stu-id="18fa9-155">The value will not be overwritten regardless of whether the message is sent to a static or dynamic send port.</span></span> <span data-ttu-id="18fa9-156">換言之，不管組態屬性設於何處，傳送管線元件都會覆寫組態屬性。</span><span class="sxs-lookup"><span data-stu-id="18fa9-156">In other words, send pipeline components overwrite the configuration property no matter where it was set.</span></span>  
  
    -   <span data-ttu-id="18fa9-157">如需自訂管線元件的詳細資訊，請參閱[開發自訂管線元件](http://go.microsoft.com/fwlink/?LinkId=155769)(http://go.microsoft.com/fwlink/?LinkId=155769)。</span><span class="sxs-lookup"><span data-stu-id="18fa9-157">For more information about custom pipeline components, see [Developing Custom Pipeline Components](http://go.microsoft.com/fwlink/?LinkId=155769) (http://go.microsoft.com/fwlink/?LinkId=155769).</span></span>  
  
    -   <span data-ttu-id="18fa9-158">如需 SOAP 傳送配接器的組態屬性的詳細資訊，請參閱[如何動態設定取用 Web 服務的 URI](http://go.microsoft.com/fwlink/?LinkID=155768) (http://go.microsoft.com/fwlink/?LinkID=155768)。</span><span class="sxs-lookup"><span data-stu-id="18fa9-158">For more information about the configuration properties of the SOAP send adapter, see [How to Dynamically Set the URI of a Consumed Web Service](http://go.microsoft.com/fwlink/?LinkID=155768) (http://go.microsoft.com/fwlink/?LinkID=155768).</span></span>  
  
-   <span data-ttu-id="18fa9-159">**加入 Web 參考加入包含多重根目錄結構描述將導致編譯錯誤的已使用的 Web 服務**</span><span class="sxs-lookup"><span data-stu-id="18fa9-159">**Adding a Web Reference to a Consumed Web Service That Contains a Multi-Rooted Schema Will Cause a Compilation Error**</span></span>  
  
     <span data-ttu-id="18fa9-160">如果您新增 Web 參考加入專案，以衍生自發佈 BizTalk 協調流程 Web 服務，且協調流程包含具有多個根節點的結構描述，然後會發生錯誤，編譯專案時。</span><span class="sxs-lookup"><span data-stu-id="18fa9-160">If you add a Web reference to your project for a Web service that was derived from a published BizTalk orchestration and the orchestration contains a schema with multiple roots, then an error will occur when the project is compiled.</span></span> <span data-ttu-id="18fa9-161">如果您將 Web 參考加入由已發佈之 BizTalk 協調流程衍生出來的專案，請確定協調流程不包含任何多重根目錄的結構描述。</span><span class="sxs-lookup"><span data-stu-id="18fa9-161">If you add a Web reference to your project that was derived from a published BizTalk orchestration, ensure that the orchestration does not contain any multi-rooted schemas.</span></span>  
  
-   <span data-ttu-id="18fa9-162">**使用 TypedDataSets 作為 Web 方法的參數**</span><span class="sxs-lookup"><span data-stu-id="18fa9-162">**Using TypedDataSets as Parameters to Web Methods**</span></span>  
  
     <span data-ttu-id="18fa9-163">當您打算使用 TypedDataSets 作為 Web 方法的參數時，需要先進行下列事項來支援此操作：</span><span class="sxs-lookup"><span data-stu-id="18fa9-163">The following is what you need to do to support using TypedDataSets as parameters to Web methods:</span></span>  
  
    1.  <span data-ttu-id="18fa9-164">將 Web 參考加入 C# 專案，然後產生 Proxy。</span><span class="sxs-lookup"><span data-stu-id="18fa9-164">Add the Web reference to a C# project and then generate the proxy.</span></span>  
  
    2.  <span data-ttu-id="18fa9-165">建立 SOAP 傳送埠，然後指定傳送埠上的 Proxy 並選擇方法。</span><span class="sxs-lookup"><span data-stu-id="18fa9-165">Create a SOAP send port and specify the proxy on the send port and choose the method.</span></span>  
  
    3.  <span data-ttu-id="18fa9-166">在協調流程中，定義晚期繫結埠與訊息類型。</span><span class="sxs-lookup"><span data-stu-id="18fa9-166">In the orchestration, define a late bound port and define the message types.</span></span> <span data-ttu-id="18fa9-167">需要沒有屬性升級或辨別的欄位存取大部分的情況下，可以定義型別為**XMLDocument**。</span><span class="sxs-lookup"><span data-stu-id="18fa9-167">For most cases where no property promotion or distinguished field access is needed, the type can be defined as **XMLDocument**.</span></span> <span data-ttu-id="18fa9-168">選取使用此類型的 PassThrough 管線。</span><span class="sxs-lookup"><span data-stu-id="18fa9-168">Select PassThrough pipelines with this type.</span></span>  
  
    4.  <span data-ttu-id="18fa9-169">在 BizTalk Server 管理主控台中，在**Web 服務**索引標籤中**SOAP 傳輸屬性**對話方塊中的 soap 傳送埠時，指定您想要使用您建立該 proxy。</span><span class="sxs-lookup"><span data-stu-id="18fa9-169">In the BizTalk Server Administration console, in the **Web Service** tab in the **SOAP Transport Properties** dialog box of the SOAP send port, specify that you want to use that proxy that you created.</span></span> <span data-ttu-id="18fa9-170">您同時需要指定組件、類型與方法。</span><span class="sxs-lookup"><span data-stu-id="18fa9-170">You will also need to specify assembly, type, and method.</span></span>  
  
-   <span data-ttu-id="18fa9-171">**加入 Web 參考加入包含需要泛型參數將導致編譯錯誤之 Web 方法的已使用的 Web 服務**</span><span class="sxs-lookup"><span data-stu-id="18fa9-171">**Adding a Web Reference to a Consumed Web Service that Contains a Web Method Expecting Generic-Based Parameters Will Cause a Compilation Error**</span></span>  
  
     <span data-ttu-id="18fa9-172">如果您加入 Web 參考加入包含需要泛型為基礎的參數，例如可為 null 的參數之 Web 方法的 Web 服務專案，編譯專案時，會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="18fa9-172">If you add a Web reference to your project for a Web service that contains a Web method expecting generic-based parameters such as nullable parameters, an error will occur when the project is compiled.</span></span> <span data-ttu-id="18fa9-173">不支援這個動作。</span><span class="sxs-lookup"><span data-stu-id="18fa9-173">This is not supported.</span></span> <span data-ttu-id="18fa9-174">您必須使用明確特製化來呼叫 XLANG/s 的泛型類別。</span><span class="sxs-lookup"><span data-stu-id="18fa9-174">You must use explicit specialization to call the generic class from XLANG/s.</span></span>  
  
-   <span data-ttu-id="18fa9-175">**使用 加入 Web 參考產生 BizTalk 結構描述**</span><span class="sxs-lookup"><span data-stu-id="18fa9-175">**BizTalk Schema Generation Using the Add Web Reference**</span></span>  
  
     <span data-ttu-id="18fa9-176">當您使用**加入 Web 參考**若要加入 Web 參考加入 BizTalk 專案，BizTalk Server 將會呼叫每個 Web 方法至結構描述所需的結構描述類型。</span><span class="sxs-lookup"><span data-stu-id="18fa9-176">When you use the **Add Web Reference**to add Web references to BizTalk projects, BizTalk Server converts the schema types that are required to call each Web method to schemas.</span></span> <span data-ttu-id="18fa9-177">BizTalk Server 會將這些結構描述加入到 Reference.xsd 中。</span><span class="sxs-lookup"><span data-stu-id="18fa9-177">BizTalk Server adds these schemas to Reference.xsd.</span></span> <span data-ttu-id="18fa9-178">若要確保**加入 Web 參考**產生 BizTalk 結構描述正確，Web 服務必須符合下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="18fa9-178">To ensure that the **Add Web Reference** generates the BizTalk schemas correctly, the Web services must conform to the following guidelines:</span></span>  
  
    -   <span data-ttu-id="18fa9-179">Web 方法應該包含**SoapDocumentMethodAttribute**而不是**SoapRpcMethodAttribute**。</span><span class="sxs-lookup"><span data-stu-id="18fa9-179">Web methods should have **SoapDocumentMethodAttribute** instead of **SoapRpcMethodAttribute**.</span></span>  
  
    -   <span data-ttu-id="18fa9-180">Web 服務和方法必須使用**常值**繫結，而不**Encoded**例如 **[SoapDocumentMethod(Use=SoapBindingUse.Literal)]**。</span><span class="sxs-lookup"><span data-stu-id="18fa9-180">Web services and methods must use the **Literal** binding instead of **Encoded** such as **[SoapDocumentMethod(Use=SoapBindingUse.Literal)]**.</span></span>  
  
    -   <span data-ttu-id="18fa9-181">Web 方法參數和傳回型別都必須有**XmlRootAttribute**的有效**命名空間**屬性除非它們是原生 XSD 類型與 XmlNode 類型。</span><span class="sxs-lookup"><span data-stu-id="18fa9-181">Web method parameters and return types must have **XmlRootAttribute** with a valid **Namespace** property unless they are native XSD types and the XmlNode type.</span></span>  
  
    -   <span data-ttu-id="18fa9-182">Web 方法不能使用**RequestNamespace**和**ResponseNamespace**中的屬性**SoapDocumentMethodAttribute**。</span><span class="sxs-lookup"><span data-stu-id="18fa9-182">Web methods must not use the **RequestNamespace** and **ResponseNamespace** properties in **SoapDocumentMethodAttribute**.</span></span>  
  
    -   <span data-ttu-id="18fa9-183">Web 服務必須符合 Web 服務互通性 (WSI) Basic Profile version 1.1。</span><span class="sxs-lookup"><span data-stu-id="18fa9-183">Web services must be compliant with the Web services interoperability (WSI) Basic Profile version 1.1.</span></span>  
  
-   <span data-ttu-id="18fa9-184">**加入 Web 參考不支援 Web 服務描述語言 (WSDL) Import 項目**</span><span class="sxs-lookup"><span data-stu-id="18fa9-184">**The Add Web Reference Does Not Support the Web Services Description Language (WSDL) Import Element**</span></span>  
  
     <span data-ttu-id="18fa9-185">當您將 Web 參考加入含有 Import 項目的 WSDL 檔案時，加入 Web 參考功能將無法運作。</span><span class="sxs-lookup"><span data-stu-id="18fa9-185">The Add Web Reference fails when you add Web references for the WSDL file with the import element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18fa9-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18fa9-186">See Also</span></span>  
 [<span data-ttu-id="18fa9-187">規劃 BizTalk Server 層</span><span class="sxs-lookup"><span data-stu-id="18fa9-187">Planning the BizTalk Server Tier</span></span>](../technical-guides/planning-the-biztalk-server-tier.md)