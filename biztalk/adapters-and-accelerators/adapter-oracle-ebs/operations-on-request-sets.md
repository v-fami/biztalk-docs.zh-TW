---
title: 要求的作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0537354d-821e-4cf9-a4d1-f4e7d1643df9
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8051a94df28df4090f78287070c5143e6f866ed7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217294"
---
# <a name="operations-on-request-sets"></a>要求的作業
在 Oracle E-business Suite 中設定的要求是一組報表和並行會組織成不同階段的程式。 您可以使用單一要求設定為執行一組報表和並行程式。 要求集劃分為一個或多個階段，而且每個階段包含一組報表和並行程式。 這些階段會彼此連結，而且每個階段執行的順序定義。 如需要求集的多個 Oracle 特定資訊，請移至[http://go.microsoft.com/fwlink/p/?LinkId=129539](http://go.microsoft.com/fwlink/p/?LinkId=129539)。  
  
 [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]可讓您執行 Oracle E-business Suite 中要求集合。 要求會公開為中的作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 要求集只包含一組並行程式，因為這些並行程式要求設定作業，就會是輸入的參數。 並行程式，以及要求設定作業會接受四個複雜型別參數和簡單的型別參數做為輸入。  
  
> [!IMPORTANT]
>  您必須針對要求設定中設定應用程式內容[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]才能執行任何作業要求集。 這是因為設定應用程式內容設定 （例如責任、 組織及語言設定） 的使用者喜好設定以及成品的存取控制有助於安全 Oracle E-business Suite 中的交易。 應用程式內容，以及如何設定它的相關資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
## <a name="complex-type-parameters"></a>複雜型別參數
  
-   **SetRelClassOptions**： 可讓您設定的要求組排程選項。 如果已設定 SetRelClassOptions 和 SetRepeatOptions SetRelClassOptions 將享有優先權。 SetRelClassOptions 接受做為參數的下列選項：  
  
    -   **應用程式**： 指出要求組相關的應用程式的簡短名稱。  
  
    -   **ClassName**： 指出要求集相關聯的類別名稱。  
  
    -   **CanceOrHold**： 指出取消 」 或 「 保留 」 旗標。  
  
    -   **StaleDate**： 指出日期要求組尚未執行，當天或之後這個將取消要求集。  
  
    -   **ContinueOnFail**： 指出要求組提交應該繼續還是 SetRelClassOptions 失敗時擲回例外狀況。 您可以指定"True"（繼續） 或"False"（擲回例外狀況）。  
  
-   **SetPrintOptions**： 可讓您設定要求集的列印選項。 SetPrintOptions 接受做為參數的下列選項：  
  
    -   **印表機**： 指出設定輸出要求應該會傳送的印表機名稱。  
  
    -   **樣式**： 指出用來列印要求設定輸出的列印樣式。 例如，您可以指定方向 （「 橫印 」 或 「 縱向 」）。  
  
    -   **複製**： 指出要設定輸出的要求列印的份數。  
  
    -   **SaveOutput**： 指出是否要儲存輸出檔案。 您可以指定"True"False"。  
  
    -   **PrintTogether**： 只適用於子要求。 表示子要求的輸出列印的方式。 如果您指定"Y"，所有的子要求已完成之後，才列印輸出的子要求。 如果您指定完成時，會列印"N"，每項子要求的輸出。  
  
    -   **ContinueOnFail**： 指出要求組提交應該繼續還是 SetPrintOptions 失敗時擲回例外狀況。 您可以指定"True"（繼續） 或"False"（擲回例外狀況）。  
  
-   **SetRepeatOptions**： 可讓您設定要求集的重複選項。 SetRepeatOptions 接受做為參數的下列選項：  
  
    -   **RepeatTime**： 指出要重複的要求集合的當日時間。  
  
    -   **RepeatInterval**： 這是參數時才適用**RepeatTime**是 NULL。 表示要求的 resubmissions 之間的間隔。 使用此選項，連同**RepeatUnit**指定 resubmissions 之間的時間。  
  
    -   **RepeatUnit**： 這是參數時才適用**RepeatTime**是 NULL。 時間與單位**RepeatInterval**若要指定要求的 resubmissions 之間的時間。 您可以指定"Minutes"、"Hours"、"Days"或"Months"。  
  
    -   **RepeatType**： 這是參數時才適用**RepeatTime**是 NULL。 指出是否將重複間隔會套用前一個要求 「 開始 」 設定執行後，或者在前一個要求 「 結束 」 設定執行。  
  
    -   **RepeatEndTime**： 指出停止重新提交要求集的日期和時間。  
  
    -   **ContinueOnFail**： 指出要求組提交應該繼續還是 SetRepeatOptions 失敗時擲回例外狀況。 您可以指定"True"（繼續） 或"False"（擲回例外狀況）。  
  
-   **SetNlsOptions**： 可讓您設定要求集 NLS 選項。 SetNlsOptions 接受做為參數的下列選項：  
  
    -   **語言**： 表示 NLS 語言。  
  
    -   **語言**： 指出語言領域。  
  
    -   **ContinueOnFail**： 指出要求組提交應該繼續還是 SetNlsOptions 失敗時擲回例外狀況。 您可以指定"True"（繼續） 或"False"（擲回例外狀況）。  
  
## <a name="simple-type-parameter"></a>簡單的型別參數
  
 **StartTime**： 表示要求集應該開始執行的時間。  
  
 如果要求設定已經順利完成，會傳回識別碼的並行要求。 否則，會傳回"0"。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)