---
title: "Web 服務的發行時的考量 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, publishing
- Web services, planning
- Web services, schemas
- schemas, Web services
ms.assetid: 3ace0260-a1cb-4e59-a820-36ee7d5cceda
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 825a16555f0b0c82282ae4d85592567d2a19c073
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-when-publishing-web-services"></a>發佈 Web 服務的考量
本主題提供發佈 Web 服務之前應考量的資訊。  
  
## <a name="publishing-schemas-and-the-include-element"></a>發佈結構描述和 include 項目  
 有幾個案例，其中結構描述包含**包含**項目不能發行為 Web 服務。 因此當您完成 [BizTalk Web 服務發佈精靈] 時，將會發生錯誤。 這些限制包括下列各項：  
  
-   循環包含 (包含結構描述具有**包含**要包含的結構描述項目)  
  
-   無法解析**schemaLocation**屬性將會產生錯誤  
  
 如需有關的限制包含項目，請參閱 < 包含的項目繫結支援 >，網址[http://go.microsoft.com/fwlink/?LinkId=62312](http://go.microsoft.com/fwlink/?LinkId=62312)。  
  
## <a name="publishing-schemas-and-the-import-element"></a>發佈結構描述和 import 項目  
 [BizTalk Web 服務發佈精靈] 與 .NET Framework 中包含的 XSD.exe 擁有相同的限制。 詳細資訊，請參閱 < 匯入項目繫結支援 >，網址[http://go.microsoft.com/fwlink/?LinkId=62311](http://go.microsoft.com/fwlink/?LinkId=62311)。  
  
## <a name="publishing-schemas-and-the-redefine-element"></a>發佈結構描述和 redefine 項目  
 [BizTalk Web 服務發佈精靈] 與 .NET Framework 中包含的 XSD.exe 擁有相同的限制。 詳細資訊，請參閱 < Redefine 項目繫結支援 >，網址[http://go.microsoft.com/fwlink/?LinkId=62313](http://go.microsoft.com/fwlink/?LinkId=62313)。  
  
## <a name="publishing-schemas-that-specify-values-for-minoccurs-or-maxoccurs-attributes"></a>發佈指定 minOccurs 或 maxOccurs 屬性值的結構描述  
 如果您發行的結構描述包含**minOccurs**或**maxOccurs**具有特定值的屬性，這些值可能不同於已發行的 Web 服務所公開的結構描述。 一般的基本原則是，所有 minOccurs 屬性都會轉換成 0 (minOccurs=0)，而 maxOccurs 屬性會轉換成 1 或未繫結 (maxOccurs=1 或 maxOccurs=unbounded)。  
  
## <a name="publishing-envelope-schemas"></a>發佈信封結構描述  
 如果您有將要發佈為 Web 服務的信封結構描述，則必須手動修改產生的 Web 專案。  
  
#### <a name="to-modify-the-generated-web-project-for-envelope-schemas"></a>若要針對信封結構描述修改所產生的 Web 專案  
  
1.  開啟 <`myWebService`>.asmx.cs 檔。  
  
2.  編輯檔案並且將 `bodyTypeAssemblyQualifiedName = <dll.name.version.>` 變更為 `bodyTypeAssemblyQualifiedName = null`。  
  
> [!NOTE]
>  如果先前的 .dll 檔案仍存在於 ASP.NET 背景工作處理序中，您可能需要重設 Internet Information Services (IIS)。  
  
## <a name="web-service-and-web-method-attributes"></a>Web 服務和 Web 方法的屬性  
 [BizTalk Web 服務發佈精靈] 不允許您自訂 ASP.NET 中使用的 Web 服務或 Web 方法的屬性。 某些屬性會根據精靈提供的資訊自動設定。 精靈不會使用其他屬性。  
  
 修改現有的屬性或新增屬性至 [BizTalk Web 服務發佈精靈] 產生的 Web 服務，可能會造成 Web 服務運作不正常。  
  
 如需 Web 服務和 Web 方法屬性的詳細資訊，請參閱**WebServiceAttribute**和**WebMethodAttribute** .NET Framework SDK 文件中的類別。  
  
## <a name="web-method-required"></a>需要 Web 方法  
 Web 服務必須至少擁有一個 Web 方法。 如果沒有 Web 方法，連接埠類型將不會建立其作業。 XLANG/s 不支援未包含作業的連接埠類型。  
  
## <a name="dbcs-character-support"></a>DBCS 字元支援  
 Web 服務不支援中文/日文/韓文 (CJK) Unified Ideograph Extension A 等字元。  
  
## <a name="republishing-web-services-using-the-biztalk-web-services-publishing-wizard"></a>使用 BizTalk Web 服務發佈精靈重新發佈 Web 服務  
 您可以使用 [BizTalk Web 服務發佈精靈] 重新發佈已發佈的 Web 服務。 在**Web * * * 服務 * * * 專案** 頁面上，您可以選取**覆寫 * * * Web * * * 服務**選項。  
  
 精靈不會儲存之前使用的設定。 如果您在重新執行精靈時變更設定，任何使用 (呼叫) 已發佈服務的 Web 用戶端都可能會失敗。 您應該更新任何使用 (呼叫) 已發佈 Web 服務之用戶端的 Web 參考。  
  
## <a name="clients-of-published-web-services-may-not-receive-server-script-timeout-errors"></a>已發佈的 Web 服務用戶端可能無法接收伺服器指令碼逾時錯誤  
 產生的 Web 服務發佈精靈，在 web 服務[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]設定預設的指令碼逾時值**110**秒。 這是 .NET Framework 的預設值。 **HttpServerUtility.ScriptTimeout**屬性。 使用.NET Framework 的 web 用戶端設定要求逾時值預設**100**秒。 這是.NET Framework 的預設值**HttpWebRequest.Timeout**屬性。  
  
 如果使用 .NET Framework 的 Web 用戶端將會呼叫以 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web 服務發佈精靈] 所產生的 Web 服務，這時因為用戶端要求逾時依預設會先行發生，所以用戶端可能就無法接收到伺服器指令碼逾時錯誤。 若要解決這個問題，您可以執行下列其中一項工作：  
  
-   用戶端要求逾時增加為大於伺服器指令碼逾時的值所增加的值**HttpWebRequest.Timeout**用戶端上的屬性。  
  
-   伺服器指令碼逾時的值減少到小於用戶端要求逾時減少可能的值**HttpServerUtility.ScriptTimeout**在伺服器上的屬性。  
  
## <a name="see-also"></a>另請參閱  
 [發佈 Web 服務](../core/publishing-web-services.md)