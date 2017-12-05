---
title: "協調流程效能最佳化 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 437c7325-f037-451a-8dbd-f8d8c8889e20
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b4f8a3b0bcc58fbed428152bb9f55c34d867258a
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="optimizing-orchestration-performance"></a>協調流程效能最佳化
本主題說明在 BizTalk Server 方案中使用協調流程的最佳作法。 這包括的建議：  
  
-   減少使用協調流程的 BizTalk Server 解決方案的延遲時間  
  
    -   消除協調流程的訊息只模式  
  
    -   利用內嵌傳送從協調流程  
  
    -   協調流程持續點最小化  
  
-   巢狀協調流程  
  
-   協調流程設計模式  
  
-   協調流程的例外狀況處理區塊  
  
## <a name="recommendations-for-optimizing-orchestrations-for-low-latency-scenarios"></a>最佳化的低延遲案例的協調流程的建議事項  
 下列技術可用來降低使用協調流程的 BizTalk Server 解決方案的延遲。  
  
### <a name="eliminate-orchestrations-for-messaging-only-patterns"></a>消除協調流程的訊息只模式  
 盡可能減少對於提高整體輸送量並降低延遲的商務程序的協調流程使用。 如果那里不需要執行長時間執行交易，而且不需要叫用每個要求的數個系統，則考慮排除協調流程，再前往接收和傳送埠，以減少往返的總數量的商務邏輯BizTalkMsgBoxDb 和減少資料庫存取造成的延遲。 在此情況下，實作自訂管線，並重複使用先前已從協調流程叫用的 helper 類別。 使用協調流程嚴格需要時才實作散佈和收集或群組的設計模式。 如需協調流程設計模式的詳細資訊，請參閱主題[實作協調流程中的設計模式](http://go.microsoft.com/fwlink/?LinkId=140042)(http://go.microsoft.com/fwlink/?LinkId=140042) 中的 BizTalk Server 文件。  
  
### <a name="use-inline-sends-from-orchestrations-to-accommodate-low-latency-scenarios"></a>使用即時從傳送協調流程以容納低延遲案例  
 您應該盡可能盡量少用的協調流程和喜好僅限傳訊模式，來提高整體輸送量並減少的商務程序的延遲。 如果不需要長時間執行的交易，而且不需要的商務邏輯來叫用數個系統，請考慮將商務邏輯來接收和傳送埠和排除的協調流程使用。 這種方法可以實作自訂管線，其重複使用先前已從協調流程叫用的 helper 類別。 為了達到較佳的效能低延遲案例，請採用下列方法之一：  
  
-   消除不必要的協調流程，並採用僅限傳訊模式，以減少到 BizTalk MessageBox 資料庫往返的總數量。 這個方法適用於低度延遲，因為內嵌傳送略過 BizTalk 傳訊引擎和相關聯的額外負荷。 協調流程內嵌傳送功能被提供使用 BizTalk Server 2006 和更新版本。  
  
-   在協調流程、 消除邏輯連接埠繫結至實體連接埠，並使用內建傳送他們的位置。 例如，內嵌傳送無法用來建立 WCF proxy 類別，以叫用下游 Web 服務或用來存取 SQL Server 資料庫的 ADO.NET 元件的執行個體。 在下列圖表中，當協調流程具現化商務元件，請在內部會使用 WCF，會執行內嵌傳送直接叫用下游 Web 服務 proxy 物件：  
  
     ![描述的 BizTalk 協調流程內嵌傳送](../technical-guides/media/inlinesend.gif "InlineSend")  
  
> [!NOTE]  
>  使用 從協調流程內嵌傳送將會大幅降低延遲，雖然有這種方法的限制。 因為內嵌傳送略過 BizTalk 傳訊引擎，不能使用與傳訊引擎提供下列功能：  
>   
>  -   交易管線  
> -   可復原管線  
> -   呼叫 BAM 攔截器 API 的管線  
> -   BizTalk Server 配接器支援  
> -   批次處理  
> -   重試次數  
> -   相互關聯集初始化  
> -   宣告式組態  
> -   次要傳輸  
> -   追蹤  
> -   BAM 的宣告方式使用  
  
 無法從協調流程內執行的管線類型的詳細資訊，請參閱本主題的 < 限制 > 一節[如何使用運算式執行管線](http://go.microsoft.com/fwlink/?LinkId=158008)(http://go.microsoft.com/fwlink/?LinkId = 158008) 中的 BizTalk Server 2010 文件。  
  
### <a name="optimize-orchestration-latency-by-reducing-the-number-of-persistence-points-if-possible"></a>協調流程延遲最佳化盡可能減少持續點的數目  
 協調流程範圍只需要標示為 「 長時間執行交易式 「 如果您想要使用補償或範圍的逾時。 長時間執行交易式範圍會造成額外的持續性端點結尾的範圍內，當您不需要使用補償或範圍逾時應該予以避免。 不可部分完成的範圍會導致在範圍結尾的持續性點，但也可保證沒有持續點會發生在不可部分完成的範圍內。 在範圍內沒有持續性此副作用有時使用對您來說批次持續點，（當執行多個傳送，例如）。 一般情況下，不過，我們建議您盡可能避免不可部分完成範圍。 協調流程引擎將儲存至持續性儲存體在不同時間點，執行中協調流程執行個體的整個狀態，讓執行個體可以稍後再還原記憶體中並執行到完成為止。   
**協調流程中的持續點數目是其中的關鍵因素影響訊息通過協調流程的延遲**。 引擎達到保存點，每次執行中協調流程的內部狀態會序列化並儲存到 MessageBox，這項作業會產生延遲的成本。 內部狀態的序列化包含所有的訊息和具現化，但尚未釋放的協調流程中的變數。 較大的訊息和變數以及這些愈多，花愈保存協調流程的內部狀態。 持續點數目過多可能會導致效能大幅降低。 基於這個理由，我們建議您排除的交易式範圍數目，從而減少不必要的持續點，從協調流程，並傳送圖形。 這個方法可讓您減少 MessageBox，因為協調流程凍結和解除凍結，增加整體的延展性，並降低延遲協調流程的爭用。   
另一個建議是永遠保留內部狀態的協調流程越小越好。 這項技術可以大幅降低 XLANG 引擎序列化、 保存及還原內部狀態的持續點發生協調流程所花費的時間。 為了達成此目的的一種方式為盡可能建立變數和訊息越和釋放它們儘早越好。如需範例導入您的協調流程內的非交易式範圍，並宣告變數和訊息，而不是最高的層級宣告就這些內部範圍內。 如需最小化協調流程持續點的詳細資訊，請參閱 BizTalk Server 2010 文件中的下列主題：  
  
-   [持續性和協調流程引擎](http://go.microsoft.com/fwlink/?LinkID=155292)(http://go.microsoft.com/fwlink/?LinkID=155292)。  
  
-   [協調流程凍結和解除凍結](http://go.microsoft.com/fwlink/?LinkID=155284)(http://go.microsoft.com/fwlink/?LinkID=155292)。  
  
## <a name="guidelines-for-using-promoted-properties-to-access-message-tags-or-attributes-from-an-orchestration"></a>使用的指導方針升級屬性，以存取訊息標記或屬性從協調流程  
 如果您需要將屬性升級，升級只會用於訊息路由、 篩選和訊息的相互關聯的屬性。 每個屬性升級需要解譯器元件 （XML、 一般，自訂），辨識文件類型，以及使用 XPath 運算式從相對的註解的 XSD 定義文件類型中所包含的訊息中擷取資料。 此外，每個屬性升級時 「 訊息代理程式 」 會將訊息發佈到 MessageBox 資料庫會導致個別 bts_InsertProperty 預存程序的呼叫。 如果協調流程需要存取特定項目或 XML 文件所包含的屬性，請使用下列技術：  
  
-   降低寫入和升級屬性的數目，並排除這些不是絕對必要。  
  
-   消除不必要的辨別的欄位。 辨別的欄位會寫入內容屬性，因為其名稱是用來擷取資料的 XPath 運算式相等，他們可以輕鬆地佔用大量空間。 辨別的屬性定義為在 XSD 中定義的文件類型的註解。 解譯器元件會使用相同的方法採用的升級屬性，並使用定義內送文件中找到它內的辨別的欄位的 XPath 運算式。 然後，解譯器元件將屬性寫入內容中位置：  
  
    -   **名稱**： 註釋中定義的 XPath 運算式。  
  
    -   **值**： 內送文件中的 XPath 運算式所識別之項目的值。  
  
     XPath 運算式很可能會很長，尤其是有問題的項目非常深入文件結構描述中。 因此比較辨別欄位，較大的內容大小。 這又會產生負面影響整體效能。  
  
-   使用協調流程執行階段所提供的 XPath 內建函數。  
  
-   如果訊息會變得很小 （幾 kb 為單位） 和 XML 格式，您還可以還原序列化訊息的.NET 類別執行個體並使用公用欄位和屬性。 如果需要複雜的細節 （自訂程式碼、 商務規則引擎原則等） 的訊息，使用.NET 類別的執行個體所公開的屬性存取資料的速度使用 XPath 運算式使用。 協調流程所叫用商務邏輯完成之後，實體物件可以序列化到 BizTalk 訊息。 您可以使用下列工具之一的 XML 結構描述建立.NET 類別： XSD 工具 (.NET Framework 2.0) 或 SVCUTIL (.NET Framework 3.0)。  
  
-   啟用從協調流程的協助程式元件。 這項技術有使用辨別的欄位的優勢。 事實上，協調流程可讀取的 XPath 運算式從設定儲存 （在組態檔、 SSO 組態存放區、 自訂 Db 等等），以便當您有變更的 XPath 運算式時，您不需要變更和重新部署結構描述時，您應該進行升級的屬性和 distinguished 欄位。 下列程式碼範例提供的協助程式元件的範例。 這個元件會使用 BizTalk 執行階段所提供的 XPathReader 類別。 這可讓閱讀文件資料流，直到找到 XPath 運算式的程式碼。  
  
```  
#region Copyright  
//===  
//Microsoft Windows Server AppFabric Customer Advisory Team (CAT)   
//  
// This sample is supplemental to the technical guidance published on the community  
// blog.  
//   
// Author: Paolo Salvatori.  
//===  
// Copyright © 2010 Microsoft Corporation. All rights reserved.  
//   
// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF ANY KIND, EITHER   
// EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE IMPLIED WARRANTIES OF   
// MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE. YOU BEAR THE RISK OF USING IT.  
//===  
#endregion  
#region Using Directives  
using System;  
using System.Collections.Generic;  
using System.IO;  
using System.Xml;  
using System.Linq;  
using System.Text;  
using System.Globalization;  
using Microsoft.XLANGs.BaseTypes;   
using Microsoft.BizTalk.Streaming;  
using Microsoft.BizTalk.XPath;  
#endregion  
namespace Microsoft.AppFabric.CAT.Samples.DuplexMEP.Helpers  
{  
public class XPathHelper  
{  
#region Private Constants   
private const string MessageCannotBeNull = "[XPathReader] The message cannot be null.";  
#endregion  
#region Public Static Methods  
public static string GetValue(XLANGMessage message, int partIndex, string xpath)  
{  
try  
{  
if (message == null)  
{  
throw new ApplicationException(MessageCannotBeNull);  
}  
using (Stream stream = message[partIndex].RetrieveAs(typeof(Stream)) as Stream)  
{  
XmlTextReader xmlTextReader = new XmlTextReader(stream);  
XPathCollection xPathCollection = new XPathCollection();  
XPathReader xPathReader = new XPathReader(xmlTextReader, xPathCollection);  
xPathCollection.Add(xpath);  
while (xPathReader.Read())  
{  
if (xPathReader.HasAttributes)  
{  
for (int i = 0; i < xPathReader.AttributeCount; i++)  
{  
xPathReader.MoveToAttribute(i);  
if (xPathReader.Match(xPathCollection[0]))  
{  
return xPathReader.GetAttribute(i);  
}  
}  
}  
if (xPathReader.Match(xPathCollection[0]))  
{  
return xPathReader.ReadString();  
}  
}  
}  
}  
finally  
{  
message.Dispose();  
}  
return string.Empty;  
}  
#endregion  
}  
}  
```  
  
## <a name="minimize-orchestration-complexity-to-improve-performance"></a>最小化協調流程的複雜度來改善效能  
 協調流程的複雜度對效能有重大影響。 當協調流程的複雜度增加，則會減少整體效能。 協調流程可用於幾乎無限的各種案例，以及每個案例可能涉及協調流程的複雜度。 避免複雜的協調流程，盡可能改用模組化的方法。 換句話說，將您的商務邏輯分割成多個可重複使用的協調流程。  
  
 如果您需要實作複雜的協調流程，定義訊息和變數，盡可能內部範圍到，而不是根層級。 這項技術會維護小的耗用量在記憶體中的每個協調流程，因為變數和訊息時進行處置的流程會離開的範圍，其中已定義的變數和訊息。 當協調流程會儲存到 MessageBox 持續點，這個方法是特別有幫助。  
  
## <a name="use-the-call-orchestration-shape-versus-the-start-orchestration-shape-to-improve-performance"></a>使用 呼叫協調流程圖形與啟動協調流程圖形來改善效能  
 避免**啟動協調流程**圖形，並使用**呼叫協調流程**執行巢狀協調流程圖形。 事實上，**呼叫協調流程**圖形可以用來同步呼叫另一個專案中參考的協調流程。 在 BizTalk 專案之間，這個方法可讓以供重複使用常見的協調流程的工作流程模式。 當您叫用另一個巢狀的協調流程的狀況下同步**呼叫協調流程**圖形，封閉式協調流程會等待巢狀協調流程完成後再繼續進行。 巢狀協調流程會執行呼叫的協調流程的相同執行緒上執行。  
  
 **啟動協調流程**圖形是類似於**呼叫協調流程**圖形，但在此情況下，巢狀協調流程會呼叫以非同步的方式： 在叫用的控制流程協調流程會繼續超出引動過程，而不需等待叫用的協調流程完成其工作。 若要實作此之間的去耦合在呼叫端和被呼叫的協調流程、**啟動協調流程**透過訊息到 BizTalk Messagebox 的發行集實作。 內含式 BizTalk 主控件執行個體執行巢狀協調流程接著會耗用此訊息。 可能的話，請使用**呼叫協調流程**，尤其是如果呼叫的協調流程需要等待巢狀協調流程的結果，才能繼續處理。  如需有關如何使用 呼叫協調流程圖形的詳細資訊，請參閱 BizTalk Server 2010 文件中的下列主題：  
  
-   [使用直接繫結連接埠在協調流程中](http://go.microsoft.com/fwlink/?LinkId=139902)(http://go.microsoft.com/fwlink/?LinkId=139902)。  
  
-   [巢狀協調流程](http://go.microsoft.com/fwlink/?LinkId=139903)(http://go.microsoft.com/fwlink/?LinkId=139903)。  
  
## <a name="use-xmlreader-with-xlangmessage-versus-using-xmlreader-with-xmldocument-to-improve-orchestration-performance"></a>使用 XmlDocument 使用 XmlReader，來改善協調流程效能與使用 XLANGMessage 的 XmlReader  
 若要改善.NET 方法，從協調流程呼叫的協調流程效能，使用 XLANGMessage，不 XmlDocument XmlReader。 下列程式碼範例將說明這項功能。  
  
```csharp  
// As a general rule, use XmlReader with XLANGMessage, not XmlDocument.   
// This is illustrated in the parameter passed into the following code.   
// The XLANG/s compiler doesn't allow a return value of XmlReader   
// so documents must be initially constructed as XmlDocument()  
public static XmlDocument FromMsg(XLANGMessage old)  
{  
    //get at the data  
    XmlDocument ret = new XmlDocument();  
  
    try{  
        XmlReader reader = (XmlReader)old[0].RetrieveAs(typeof(XmlReader));  
        //construct new message from old  
        //read property  
        object msgid = old.GetPropertyValue(typeof(BTS.MessageID));  
    }  
    finally {  
        // Call Dispose on the XLANGMessage object   
        // because the message doesn't belong to the   
        // .NET runtime - it belongs to the Messagebox database   
        old.Dispose();  
    }  
    return ret;  
}  
```  
  
 另一個方法，可建立結構描述為基礎的.NET 類別。 這個動作所花較少的記憶體比載入文件至**XmlDocument**物件，以及讓您輕鬆存取結構描述項目適用於.NET 開發人員。 若要產生 BizTalk 結構描述為基礎的類別，您可以使用 Visual Studio 提供的 xsd.exe 工具。 例如，執行**xsd.exe \<schema.xsd\> /類別**針對簡單的結構描述，其中包含名為 ItemA 的欄位，ItemB，ItemC，將會產生下列類別。  
  
```csharp  
//------------------------------------------------------------------------------  
// <auto-generated>  
//     This code was generated by a tool.  
//     Runtime Version:2.0.50727.1433  
//  
//     Changes to this file may cause incorrect behavior and will be lost if  
//     the code is regenerated.  
// </auto-generated>  
//------------------------------------------------------------------------------  
  
using System.Xml.Serialization;  
  
//   
// This source code was auto-generated by xsd, Version=2.0.50727.42.  
//  
  
/// <remarks/>  
[System.CodeDom.Compiler.GeneratedCodeAttribute("xsd", "2.0.50727.42")]  
[System.SerializableAttribute()]  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.ComponentModel.DesignerCategoryAttribute("code")]  
[System.Xml.Serialization.XmlTypeAttribute(AnonymousType=true, Namespace="http://Schemas.MySchema")]  
[System.Xml.Serialization.XmlRootAttribute(Namespace="http://Schemas.MySchema", IsNullable=false)]  
public partial class MySchemaRoot {  
  
    private string itemAField;  
  
    private string itemBField;  
  
    private string itemCField;  
  
    /// <remarks/>  
    [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified)]  
    public string ItemA {  
        get {  
            return this.itemAField;  
        }  
        set {  
            this.itemAField = value;  
        }  
    }  
  
    /// <remarks/>  
    [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified)]  
    public string ItemB {  
        get {  
            return this.itemBField;  
        }  
        set {  
            this.itemBField = value;  
        }  
    }  
  
    /// <remarks/>  
    [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified)]  
    public string ItemC {  
        get {  
            return this.itemCField;  
        }  
        set {  
            this.itemCField = value;  
        }  
    }  
}  
```  
  
 這個類別可以參考您的.NET 組件才能存取的訊息項目，並傳回的物件可以直接指派給訊息。 以下是類別的範例使用上面所產生。  
  
```csharp  
public static Root SetValues(Microsoft.XLANGs.BaseTypes.XLANGMessage msg)  
{  
   try  
   {  
   MySchemaRoot rootObj=(MySchemaRoot)msg[0].RetrieveAs(typeof(MySchemaRoot);  
   rootObj.ItemA="value a";  
   rootObj.ItemB="value b";  
   rootObj.ItemC="value c";  
   }  
    finally {  
        msg.Dispose();  
            }  
  
   return rootObj;  
}  
```  
  
 這項技術可讓您處理訊息時使用的物件導向的方法。 應該使用這項技術，主要被使用相對較小的訊息。 這是因為即使這項技術會使用比時載入至訊息大幅減少記憶體**XmlDocument**物件時，整個訊息仍然會載入記憶體。 處理較大的訊息時，使用**XmlReader**讀取訊息的類別和**XmlWriter**類別來寫入訊息。 當使用**XmlReader**和**XmlWriter**，訊息會包含在**VirtualStream**物件。 如果訊息大小超過指定的值**大型訊息閾值 （位元組）**公開 BizTalk 群組屬性的 [設定] 頁面上，將訊息寫入至檔案系統。 這會降低整體效能，但可避免記憶體不足例外狀況。  
  
## <a name="improve-performance-by-minimizing-the-use-of-logical-ports-bound-to-physical-ports"></a>最小化的邏輯連接埠繫結至實體連接埠使用來改善效能  
 您可以藉由減少使用的繫結至實體連接埠，使用下列介面卡的邏輯連接埠來提升效能：  
  
-   SQL Server、 Oracle  
  
-   WSE，HTTP，WCF  
  
-   MSMQ、 MQSeries  
  
 在 BizTalk Server 2010 中，傳送和接收管線直接叫用協調流程中使用包含在 Microsoft.XLANGs.Pipeline.dll XLANGPipelineManager 類別。 因此，處理管線的可移動連接埠至協調流程。協調流程中的邏輯連接埠可以取代為 「 運算式 」 圖形，叫用指定的.NET 類別的執行個體 （例如，使用 ADO.NET 資料存取元件）。 採用這項技術之前, 您應該注意，如果您未使用介面卡和實體連接埠，就會失去運用其功能，例如批次，重試、 宣告式組態，以及次要傳輸的能力。  
  
## <a name="orchestration-design-patterns"></a>協調流程設計模式  
 協調流程設計師 」 可讓開發人員實作各種不同的企業整合模式。 一些常見的模式包括彙總工具、 例外狀況處理和補償、 訊息代理人、 散佈和收集，並循序和平行群組。 若要開發複雜的企業應用程式整合 (EAI)、 Service-Oriented 架構 (SOA) 和商務程序管理 (BPM) 解決方案與 BizTalk Server 可以利用這些模式。 如需協調流程設計模式的詳細資訊，請參閱主題[實作協調流程中的設計模式](http://go.microsoft.com/fwlink/?LinkId=140042)(http://go.microsoft.com/fwlink/?LinkId = 140042) 中的 BizTalk Server 文件和[模式以及企業整合的最佳作法](http://go.microsoft.com/fwlink/?LinkId=140043)(http://go.microsoft.com/fwlink/?LinkId = 140043)。  
  
## <a name="make-appropriate-use-of-net-classes-in-orchestrations-to-maximize-performance"></a>請將效能最大化的協調流程中使用適當的.NET 類別  
 一般情況下，協調流程內使用的.NET 類別可以分成兩個不同的類別：  
  
-   **協助程式和服務-**這些類別會提供一般服務至協調流程，例如追蹤、 錯誤處理、 快取，以及序列化/還原序列化。 大部分的這些類別可以實作做為靜態類別沒有任何內部狀態與多個公用靜態方法。 這個方法可避免在相同的時間，可協助降低主機處理程序的工作空間，並節省記憶體執行不同的協調流程中建立多個物件相同的類別。 是無狀態的類別，有助於減少必須序列化和凍結的協調流程時，保存到 BizTalk MessageBox 的內部狀態的整體大小。  
  
-   **實體和商務物件-**您可以使用這些類別來管理實體，例如訂單、 訂單項目，以及客戶。 單一協調流程可以在內部建立和管理多個相同的型別執行個體。 這些類別通常可以設定狀態，並且公開公用欄位和/或屬性，以及修改物件的內部狀態的方法。 這些類別的執行個體可以動態地還原 XLANGMessage 部分序列化至.NET 物件，藉由建立**XmlSerializer**或**DataContractSerializer**使用或類別**XLANGPart.RetrieveAs**方法。 您應該建構協調流程中使用非交易式範圍的方式，建立盡可能晚期和釋出不再需要為可設定狀態之類別的執行個體。 這個方法可減少主機處理程序的工作空間，並會序列化並保存到 MessageBox 資料庫中，已凍結的協調流程時的內部狀態的整體大小降到最低。 如需有關如何使用 BizTalk Server 中的協調流程的詳細資訊，請參閱文章[BizTalk Server 協調流程的常見問題集](http://go.microsoft.com/fwlink/?LinkID=116886)(http://go.microsoft.com/fwlink/?LinkID=116886)。  
  
    > [!NOTE]  
    >  雖然這篇文章針對 BizTalk Server 2004 和 BizTalk Server 2006 所撰寫，所呈現的概念也適用於 BizTalk Server 2010 協調流程。  
  
## <a name="orchestration-exception-handler-blocks"></a>協調流程例外狀況處理常式區塊  
 使用協調流程例外狀況處理常式區塊，在一或多個領域 （盡可能非交易式範圍） 中包含所有的協調流程圖形，並至少建立下列的例外狀況處理常式區塊：  
  
-   處理一般 System.Exception 錯誤例外狀況處理常式區塊。  
  
-   處理才能攔截和處理的 unmanaged 的錯誤的詳細資訊，例如 COM 例外狀況的一般例外狀況的例外狀況處理常式區塊。  
  
 如需有關如何使用協調流程的例外狀況處理區塊的詳細資訊，請參閱下列文章：  
  
-   [使用 BizTalk Server 例外狀況處理](http://msdn.microsoft.com/library/aa561229.aspx)(http://msdn.microsoft.com/library/aa561229.aspx)。  
  
-   [Charles Young 部落格、 BizTalk Server 2006： 補償模型](http://go.microsoft.com/fwlink/?LinkId=158017)(http://go.microsoft.com/fwlink/?LinkId=158017)。  
  
    > [!NOTE]  
    >  雖然這篇部落格以寫入[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]納入考量，部落格中所述的原則也適用於 BizTalk Server。  
  
## <a name="considerations-when-using-maps-in-orchestrations"></a>使用協調流程中的對應時的考量  
 在協調流程中使用對應時，就會適用下列考量：  
  
-   如果您使用對應擷取或設定屬性搭配協調流程中的商務邏輯使用辨別的欄位或升級屬性。 應該遵循此做法，因為當擷取或設定值，以對應文件載入記憶體，不過當使用辨別欄位或升級屬性時，協調流程引擎存取訊息內容並不會載入到記憶體中的文件。  
  
-   若您使用對應將數個欄位彙總成一個欄位，請使用辨別欄位或升級屬性搭配協調流程變數，以累計結果集。  
  
## <a name="see-also"></a>請參閱  
 [最佳化效能](../technical-guides/optimizing-performance.md)