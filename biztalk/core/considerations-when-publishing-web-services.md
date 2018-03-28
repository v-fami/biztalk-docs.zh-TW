---
title: Web 服務的發行時的考量 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- schemas, publishing
- Web services, planning
- Web services, schemas
- schemas, Web services
ms.assetid: 3ace0260-a1cb-4e59-a820-36ee7d5cceda
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 825a16555f0b0c82282ae4d85592567d2a19c073
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="considerations-when-publishing-web-services"></a>發佈 Web 服務的考量
이 항목은 웹 서비스를 게시하기 전에 고려해야 할 정보를 제공합니다.  
  
## <a name="publishing-schemas-and-the-include-element"></a>스키마 게시 및 include 요소  
 有幾個案例，其中包含結構描述位置 **包括** 項目不能發行為 Web 服務。 오류는 BizTalk 웹 서비스 게시 마법사를 완료할 때 발생하며, 이러한 제한에는 다음이 포함됩니다.  
  
-   包含循環 (包含結構描述具有 **包括** 項目，包括結構描述)  
  
-   無法解析 **schemaLocation** 屬性會造成錯誤  
  
 如需有關的限制包含項目，請參閱 < 包含的項目繫結支援 >，網址[ http://go.microsoft.com/fwlink/?LinkId=62312 ](http://go.microsoft.com/fwlink/?LinkId=62312)。  
  
## <a name="publishing-schemas-and-the-import-element"></a>스키마 게시 및 import 요소  
 BizTalk 웹 서비스 게시 마법사에는 .NET Framework에 포함된 XSD.exe와 같은 제한 사항이 있습니다. 詳細資訊，請參閱 < 匯入項目繫結支援 >，網址[ http://go.microsoft.com/fwlink/?LinkId=62311 ](http://go.microsoft.com/fwlink/?LinkId=62311)。  
  
## <a name="publishing-schemas-and-the-redefine-element"></a>스키마 게시 및 redefine 요소  
 BizTalk 웹 서비스 게시 마법사에는 .NET Framework에 포함된 XSD.exe와 같은 제한 사항이 있습니다. 詳細資訊，請參閱 < Redefine 項目繫結支援 >，網址[ http://go.microsoft.com/fwlink/?LinkId=62313 ](http://go.microsoft.com/fwlink/?LinkId=62313)。  
  
## <a name="publishing-schemas-that-specify-values-for-minoccurs-or-maxoccurs-attributes"></a>minOccurs 또는 maxOccurs 특성의 값을 지정하는 스키마 게시  
 如果您要發行的結構描述包含 **minOccurs** 或 **maxOccurs** 具有特定值的屬性，這些值可能不同於已發行的 Web 服務所公開的結構描述。 경험을 바탕으로 한 일반적 규칙으로, 모든 minOccurs 특성은 0(minOccurs=0)으로 변환되고 maxOccurs 특성은 1 또는 unbounded(maxOccurs=1 or maxOccurs=unbounded)로 변환됩니다.  
  
## <a name="publishing-envelope-schemas"></a>봉투(Envelope) 스키마 게시  
 웹 서비스로 게시 중인 봉투(Envelope) 스키마가 있으면 생성된 웹 프로젝트를 수동으로 수정해야 합니다.  
  
#### <a name="to-modify-the-generated-web-project-for-envelope-schemas"></a>봉투(Envelope) 스키마에 대해 생성된 웹 프로젝트를 수정하려면  
  
1.  <`myWebService`>.asmx.cs 파일을 엽니다.  
  
2.  파일을 편집하여 `bodyTypeAssemblyQualifiedName = <dll.name.version.>`을 `bodyTypeAssemblyQualifiedName = null`로 변경합니다.  
  
> [!NOTE]
>  이전 .dll이 여전히 ASPNET 작업자 프로세스에 있는 경우 IIS(인터넷 정보 서비스)를 다시 설정해야 할 수 있습니다.  
  
## <a name="web-service-and-web-method-attributes"></a>웹 서비스 및 웹 메서드 특성  
 [BizTalk Web 服務發佈精靈] 不允許您自訂 ASP.NET 中使用的 Web 服務或 Web 方法的屬性。 某些屬性會根據精靈提供的資訊自動設定。 나머지 특성은 마법사에서 사용되지 않습니다.  
  
 기존 특성을 수정하거나 BizTalk 웹 서비스 게시 마법사가 생성하는 웹 서비스에 새 특성을 추가하면 웹 서비스가 제대로 작동하지 않을 수 있습니다.  
  
 如需 Web 服務和 Web 方法屬性的詳細資訊，請參閱 **WebServiceAttribute** 和 **WebMethodAttribute** 的.NET Framework SDK 文件中的類別。  
  
## <a name="web-method-required"></a>웹 메서드 필요  
 웹 서비스 하나에는 적어도 하나의 웹 메서드가 필요합니다. 웹 메서드가 없으면 포트 유형이 작업을 만들지 못합니다. XLANG/s는 작업이 없는 포트 유형을 지원하지 않습니다.  
  
## <a name="dbcs-character-support"></a>DBCS 문자 지원  
 웹 서비스는 CJK(중국어/일본어/한국어) 통합 표의 문자 확장 A 문자를 지원하지 않습니다.  
  
## <a name="republishing-web-services-using-the-biztalk-web-services-publishing-wizard"></a>BizTalk 웹 서비스 게시 마법사를 사용하여 웹 서비스 다시 게시  
 BizTalk 웹 서비스 게시 마법사를 사용하여 게시된 웹 서비스를 다시 게시할 수 있습니다. 在 **Web * * * Service * * * 專案**  頁面上，您可以選取 **覆寫 * * * Web * * * 服務** 選項。  
  
 마법사는 이전에 사용한 설정을 저장하지 않습니다. 마법사를 다시 실행할 때 설정을 변경하면 게시된 웹 서비스를 소비(호출)하는 웹 클라이언트에서 오류가 발생합니다. 이를 해결하려면 다시 게시된 웹 서비스를 소비(호출)하는 클라이언트의 웹 참조를 업데이트해야 합니다.  
  
## <a name="clients-of-published-web-services-may-not-receive-server-script-timeout-errors"></a>게시된 웹 서비스의 클라이언트는 서버 스크립트 시간 제한 오류를 수신하지 않음  
 產生的 Web 服務發佈精靈，在 web 服務[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]設定預設的指令碼逾時值**110**秒。 .NET Framework의 기본값입니다. **HttpServerUtility.ScriptTimeout** 屬性。 使用.NET Framework 的 web 用戶端設定預設會使用要求的逾時值的 **100** 秒。 這是.NET Framework 的預設值 **HttpWebRequest.Timeout** 屬性。  
  
 如果使用 .NET Framework 的 Web 用戶端將會呼叫以 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web 服務發佈精靈] 所產生的 Web 服務，這時因為用戶端要求逾時依預設會先行發生，所以用戶端可能就無法接收到伺服器指令碼逾時錯誤。 이 문제를 해결하려면 다음 중 하나를 수행합니다.  
  
-   增加用戶端要求逾時的值大於伺服器指令碼逾時的值 **HttpWebRequest.Timeout** 用戶端上的屬性。  
  
-   藉由減少的值減少為小於用戶端要求逾時的伺服器指令碼逾時值 **HttpServerUtility.ScriptTimeout** 伺服器上的屬性。  
  
## <a name="see-also"></a>另請參閱  
 [發佈 Web 服務](../core/publishing-web-services.md)