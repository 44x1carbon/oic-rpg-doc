# リンク
- [ギルドメンバーの新規登録](#ギルドメンバーの新規登録)

# ギルドメンバーの新規登録

```uml
@startuml{plantuml_seq_sample.png}
skinparam backgroundColor #FAFAFA
hide footbox
title ギルドメンバーの新規登録



participant GuildMemberService as main <<Service>>
[-> main: registerGuildMember(\n string $studentNumber, \n string $courseId, \n string $genderType, \n string $mailAddress, \n string $introduction \n)

create StudentNumber <<VO>>
main -> StudentNumber: new(string $code)

participant GuildMemberRepository <<Repository>>
main -> GuildMemberRepository: existStudentNumber(StudentNumber $studentNumber)
main <-- GuildMemberRepository: bool

alt Not exsit student number
  [<-- main: throw Exception
end

create CourseId <<VO>>
main ->CourseId: new(string $code)

participant CourseRepository <<Repository>>
main -> CourseRepository: existId(CourseId $courseId)
main <-- CourseRepository: bool

alt Not exsit course id
  [<-- main: throw Exception
end

create Gender <<VO>>
main ->Gender: new(string $type)

create MailAddress <<VO>>
main -> MailAddress: new(string $address)

create GuildMember <<Entity>>
main -> GuildMember: new(StudentNumber $studentNumber, CourseId $courseId, Gender $gender, MailAddress $mailAddress, string $introduction)

main -> GuildMember: id()
main <-- GuildMember: StudentNumber

[<-- main: StudentNumber
@enduml
```