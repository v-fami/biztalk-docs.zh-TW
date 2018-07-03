---
title: 在並行程式的作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bbc40e4c-d5a1-4763-9683-09a744e5b656
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a07e1cb6597a90687865932fcd2d2ce7e0e476af
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999993"
---
# <a name="operations-on-concurrent-programs"></a>並行程式的相關作業
Oracle E-business Suite 中的並行程式顯示中的作業為[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]。  Oracle 應用程式特有的並行程式以及[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]也會呈現下列三個標準作業： Get_Status、 Wait_For_Request 和 Submit_Request。 這表示如果 Oracle 應用程式有兩個同時執行的程式，將會公開作業有五種： 一個用於每個並行處理的程式，三個用於標準的作業。  
  
 如需詳細資訊：  
  
- 瀏覽和搜尋同時執行的程式，請參閱[瀏覽、 搜尋及取得 Oracle E-business 作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md)。  
  
- 如何叫用同時執行的程式中[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 <<c2> [ 叫用 Oracle E-business Suite 使用 BizTalk Server 中的並行程式](../../adapters-and-accelerators/adapter-oracle-ebs/run-concurrent-programs-in-oracle-e-business-suite-using-the-wcf-service-model.md)。  
  
> [!IMPORTANT]
>  您必須設定應用程式內容中的並行程式[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]執行並行程式中的任何作業之前。 這是因為設定應用程式內容設定 （例如責任、 組織及語言設定） 的使用者喜好設定和成品的存取控制有助於安全 Oracle E-business Suite 中的交易。 應用程式內容，以及如何將它設定的相關資訊，請參閱設定應用程式內容[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
 下列各節提供有關所公開的作業資訊[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]如同時執行的程式。  
  
##  <a name="Concurrent"></a> < Concurrent_Program_Name > 作業  
 如先前所述，將會有為數個 Oracle 應用程式中的並行程式的多個 < Concurrent_Program_Name > 作業。 < Concurrent_Program_Name > 作業會採用標準的五個參數： 三個複雜型別和兩個簡單的類型。  
  
> [!NOTE]
>  並行程式不會公開其中繼資料、 Oracle E-business 配接器會公開這些並行程式的每個 100 的選擇性參數。 已成功叫用這些並行程式，使用者必須請參閱 Oracle E-business Suite 文件，找出需要值，並行處理程式的參數，且然後將其指定。 這類並行程式的範例**日誌匯入**(實際名稱： **GLLEZL**) 中**一般分類帳**應用程式。  
  
 **複雜型別參數**  
  
- **SetOptions**： 可讓您提交要求之前設定並行處理程式的選項。 SetOptions 接受做為參數的下列選項：  
  
  -   **隱含**： 指出是否要顯示 Oracle E-business Suite 中的使用者的並行要求表單中的 並行要求。 您可以指定下列四個值之一：**否**，**是**，**錯誤**或是**警告**。 指定**No**會導致要在 Oracle E-business Suite 中的使用者的並行要求表單中顯示的要求。 指定**是**表示要求，可能只能從系統管理員的權限的並行要求表單中檢視。 指定**錯誤**會導致要求失敗時，才會顯示在使用者的並行要求表單中。 指定**警告**會要求顯示在使用者的並行要求表單只有當它沒有警告或錯誤。  
  
  -   **受保護的**： 指出是否要將並行要求保護針對使用 Oracle E-business Suite 中的並行要求表單所做的更新。 您可以指定 **[是]** （保護） 或**No** （未受保護）。  
  
  -   **語言**： 表示的國家語言支援 (NLS) 語言。 如果未不指定任何值，則會預設為目前的語言。  
  
  -   **國家/地區**： 表示的語言國家/地區。 如果未不指定任何值，則會預設為目前的語言地區。  
  
  -   **ContinueOnFail**： 指出並行要求送出作業應該繼續還是擲回例外狀況，萬一**SetOptions**失敗。 您可以指定**真**（繼續） 或**False** （擲回例外狀況）。  
  
- **SetPrintOptions**： 可讓您提交要求之前設定並行處理程式的列印選項。 SetPrintOptions 接受做為參數的下列選項：  
  
  -   **印表機**： 表示並行要求的輸出應該傳送位置的印表機名稱。 如果已經設定 Oracle E-business Suite 中的並行程式表單中，您無法覆寫此列印選項。  
  
  -   **樣式**： 指出用來將並行要求輸出列印的列印樣式。 例如，您可以在其中指定方向 (**橫向**或是**直向**)。 如果已設定的列印樣式並行程式形式在 Oracle E-business Suite 中，而**所需的樣式**核取方塊已選取，您無法覆寫此列印選項。  
  
  -   **複製**： 指出要並行要求輸出的列印的份數。  
  
  -   **SaveOutput**： 指出是否要儲存輸出檔案。 您可以指定 **[是]** 或是**No**。  
  
  -   **PrintTogether**： 只適用於包含子要求這些要求。 表示子要求的輸出列印的方式。 如果您指定**Y**，只有當所有的子要求都完成之後，才能列印輸出的子要求。 如果您指定**N**，每項子要求的輸出會列印完成。  
  
  -   **ContinueOnFail**： 指出並行要求送出作業應該繼續還是擲回例外狀況，萬一**SetPrintOptions**失敗。 您可以指定**真**（繼續） 或**False** （擲回例外狀況）。  
  
- **SetRepeatOptions**： 可讓您設定並行處理程式的重複選項，再提交要求。 **SetRepeatOptions**會做為參數的下列選項：  
  
  -   **RepeatTime**： 指出重複的並行要求的時間。  
  
  -   **RepeatInterval**： 這個參數是時才適用**RepeatTime**是 NULL。 表示要求的 resubmissions 之間的間隔。 使用此選項，連同**RepeatUnit**指定 resubmissions 之間的時間。  
  
  -   **RepeatUnit**： 這個參數是時才適用**RepeatTime**是 NULL。 搭配使用的時間單位**RepeatInterval**若要指定要求的 resubmissions 之間的時間。 您可以指定**分鐘**，**小時**，**天**或是**月**。  
  
  -   **RepeatType**： 這個參數是時才適用**RepeatTime**是 NULL。 指出是否要在並行要求執行的"end"或並行要求執行的 「 開始 」 之後，套用重複的間隔。  
  
  -   **RepeatEndTime**： 指出停止重新提交的並行要求的日期和時間。  
  
  -   **ContinueOnFail**： 指出並行要求送出作業應該繼續還是擲回例外狀況，萬一**SetRepeatOptions**。 您可以指定**真**（繼續） 或**False** （擲回例外狀況）。  
  
  **簡單的型別參數**  
  
- **描述**： 並行要求的描述。  
  
- **StartTime**： 表示並行的要求應該開始執行的時間。  
  
## <a name="getstatus-operation"></a>Get_Status 作業  
 標準作業，也就是 Get_Status，傳回要求階段/狀態和完成訊息的並行處理程式。 這項作業會採用並行處理程式的要求識別碼 (**RequestID**) 做為輸入，然後傳回下列資訊：  
  
-   **階段**： 從 FND_LOOKUPS 的使用者易記的要求階段。  
  
-   **狀態**: FND_LOOKUPS 的使用者易記的要求狀態。  
  
-   **DevPhase**: 「 要求 」 階段，可用於程式邏輯比較的字串。  
  
-   **DevStatus**： 要求的狀態，可用於程式邏輯比較的字串。  
  
-   **訊息**： 完成訊息，如果要求已完成。  
  
## <a name="waitforrequest-operation"></a>Wait_For_Request 作業  
 標準作業，也就是 Wait_For_Request，等候要求完成，並傳回要求階段/狀態和完成訊息。 這項作業會採用並行處理程式的要求識別碼 (**RequestID**)，檢查之間要等候的秒數 (**間隔**)，並以秒為單位，等候要求完成 （最長的時間**MaxWait**) 做為輸入參數，然後傳回如同 Get_Status 作業相同的資訊。  
  
## <a name="submitrequest-operation"></a>Submit_Request 作業  
 標準作業，也就是 Submit_Request，提交並行的管理員所處理的並行要求。 如果順利完成要求，此作業會傳回並行的要求識別碼。 否則，它會傳回"0"。  
  
 Submit_Request 作業採用六個標準的參數： 三個每個複雜型別的簡單型別。 除了這些參數，它也會並行處理程式的引數為字串的陣列。  
  
 **複雜型別參數**  
  
 Submit_Request 作業耗費**SetOptions**， **SetPrintOptions**，並**SetRepeatOptions**做為輸入參數。 如需這些參數的詳細資訊，請參閱[ &lt;Concurrent_Program_Name&gt;作業](#Concurrent)稍早在這一節。  
  
 **簡單的型別參數**  
  
-   **程式**： 提交要求的並行程式的簡短名稱。  
  
-   **描述**： 並行要求的描述。  
  
-   **StartTime**： 並行的要求應該開始執行的時間。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)