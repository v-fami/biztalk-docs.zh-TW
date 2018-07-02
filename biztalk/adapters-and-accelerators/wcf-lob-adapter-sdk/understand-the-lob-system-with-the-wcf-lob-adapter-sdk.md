---
title: 了解 WCF LOB 配接器 SDK 與 LOB 系統 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0f97846-5ef2-4530-853a-fba5469156f7
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a3cb898643e8a7eff1b73a138f98f1ecfc05248
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993127"
---
# <a name="understand-the-lob-system-with-the-wcf-lob-adapter-sdk"></a>了解 LOB 系統與 WCF LOB 配接器 SDK
開發您的配接器使用之前[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，您必須擁有目標的特定業務系統徹底了解。 如果您不了解特定業務系統、 的公開方式，並提供安全性、 交易和其他功能的支援不同層級所提供的功能，您的配接器可能不會提供配接器所需的功能取用者。 本章節描述您必須了解有效地設計您的配接器的區域。  
  
## <a name="the-path-to-understanding"></a>了解到的路徑  
 配接器的目的是要以一致、 可存取的方式，根據配接器規格和/或配接器 API 所加諸的規則，公開資料和從特定業務系統的作業。 若要知道哪些作業與要公開的資料，您必須了解系統的用途以及它如何公開其資料和作業。 特別是，您必須考慮下列的設計問題︰  
  
- **連接生命週期。** 連線方式開啟和關閉嗎？ 如何維護的開放連線嗎？ 有的重複使用連接的特殊需求嗎？ 如需連線的詳細資訊，請參閱`Microsoft.ServiceModel.Channels.Common.IConnection`。  
  
- **作業和型別公開的中繼資料系統。** 特定業務系統支援作業搜尋和瀏覽並方便存取的中繼資料，或您必須開發支援程式碼，以提供這項功能嗎？ 例如，SQL Server 中作業是物件，例如預存程序。 相關資料行、 資料表和其他物件的型別中繼資料可輕鬆地擷取。 舊有的業務系統可能更難以使用。  
  
- **如何操作和資料會公開由系統中。** 如何公開 API？ API 支援封鎖 （同步） 和非封鎖 （非同步） 呼叫？ 回呼支援？ 您將介面 API 或通訊協定層級嗎？  
  
- **安全性、 交易和可靠傳訊的支援。** 如果此 API 支援任何一項功能，您可能想要將它們公開到配接器取用者。 例如，SQL Server 有安全性和交易支援，不過可信賴傳訊不可行 （但會使用 MSMQ 或某些其他佇列的系統）。  
  
- **哪些功能和使用方式情節之所以如此重要？** 不要限制您了解到純技術;討論，並擷取與有經驗的使用者的商務需求。 是否有任何加諸於某些作業的唯一條件約束？ 是否有尚難以理解的作業很有用？ 某些功能很少使用？  
  
  若要探索這項資訊，您應該目標的特定業務系統的查閱的使用者和技術文件。 如果文件是疏鬆或遺失，您也可以藉由尋找線上支援論壇、 線上新聞群組、 部落格，或藉由檢查安裝檔案的實作詳細資料，深入了解系統的技術層面。 如果您有特定的業務開發人員或程式碼檔案的存取權，您可以探索您需要連接語意、 支援的安全性，以及如何搜尋及叫用作業會包括的資訊。  
  
## <a name="see-also"></a>另請參閱  
 [規劃和設計您的配接器使用 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-your-adapter-using-the-wcf-lob-adapter-sdk.md)   
 [開始使用 WCF LOB 配接器 sdk](../../adapters-and-accelerators/wcf-lob-adapter-sdk/get-started-with-the-with-the-wcf-lob-adapter-sdk.md)   
 [選取適當的架構](https://msdn.microsoft.com/library/bb798089.aspx)