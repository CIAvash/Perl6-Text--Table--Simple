# NAME

Text::Table::Simple - Create basic tables from a two dimensional array.


# SYNOPSIS

    use Text::Table::Simple;

    my @columns = ['id','name','email'];
    my @rows   = (
        [1,"John Doe",'johndoe@cpan.org'],
        [2,'Jane Doe','mrsjanedoe@hushmail.com'],
    );

    my @table = lol2table(@columns,@rows);
    $_.say for @table;

    # O----O----------O-------------------------O
    # | id | name     | email                   |
    # |-----------------------------------------|
    # | 1  | John Doe | johndoe@cpan.org        |
    # | 2  | Jane Doe | mrsjanedoe@hushmail.com |
    # O----O----------O-------------------------O


# DESCRIPTION

Output table headers and rows. Take showing your Benchmark output for example:

    use Text::Levenshtein::Damerau; 
    use Text::Table::Simple;
    use Benchmark;

    my %results = timethese($runs, {
        'dld     ' => sub { Text::Levenshtein::Damerau::{"&dld($str1,$str2)"} },
        'ld      ' => sub { Text::Levenshtein::Damerau::{"&ld($str1,$str2)"}  },
    });

    my @headers = ['func','start','end','diff','avg'];
    my @rows    = %results.map({ [.key,.value.list] });

    my @table = lol2table(@headers,@rows);

    $_.say for @table;


# METHODS

## lol2table (@header_rows,@body_rows?,@footer_rows?)

Create a an array of strings that can be printed line by line to create a table view of the data.


# TODO

## as_table

Arguments: \@rows 2 dimentional array ref 
$rows: 2 dimentional array ref
- _OPTIONAL argument_ \@columns: Header column names 
- _OPTIONAL argument_ \%format: Formatting options 

Prints out the 2D array as a table.

    @some_array.as_table(rows => @rows);
    # or maybe @some_array.as_table(headers => @headers);

## options

Allow changing the borders, corner markers, etc


# BUGS

Please report bugs to:

[https://github.com/ugexe/Perl6-Text--Table--Simple/issues](https://github.com/ugexe/Perl6-Text--Table--Simple/issues)

# AUTHOR

Nick Logan <`ugexe@cpan.org`\>
